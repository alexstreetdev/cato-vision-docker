FROM microsoft/dotnet:2.2-sdk as builder

RUN git clone https://github.com/alexstreetdev/cato-vision.net

WORKDIR ./cato-vision.net/ImageStore/ImageStore

RUN dotnet restore ImageStore.csproj

FROM builder as publish
RUN dotnet publish -c release -o output

FROM microsoft/dotnet:2.2-aspnetcore-runtime as runtime

WORKDIR /img

COPY --from=publish ./cato-vision.net/ImageStore/ImageStore/output ./

ENTRYPOINT ["dotnet", "ImageStore.dll"]
