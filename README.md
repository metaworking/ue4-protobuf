### What is this?

This is an Unreal Engine 4 plugin that integrates [Protobuf](https://github.com/protocolbuffers/protobuf) into the project without requiring you to add system PATH or anything else.

### How do use?

1. add the plugin to the project and enable it.
2. add the following property to `build.cs` of modules :

```csharp
PublicDependencyModuleNames.Add("Protobuf");
```

4. Create `.proto` file into project source code folder 
5. Launch the Project in Editor, Click the `Protoc` button.

### Protobuf Versions

- Protobuf v3.21.5
- Protobuf v3.5.1

### Upgrade Protobuf
For protobuf v3.21.x
#### 1. Clone [Protobuf](https://github.com/protocolbuffers/protobuf) repo

1. Clone to disk `git clone https://github.com/protocolbuffers/protobuf`
2. Switch to your desired branchs/tags `git checkout <branchs/tags>`

#### 2. Convert Protobuf Source

1. Use [adapte script](https://github.com/metaworking/adapt-protobuf-to-ue) to convert protobuf source
2. Copy the conversion result to `Source/Protobuf/ThirdParty/google` in **ue4-protobuf dir** 

#### 3. Compile Protoc

1. Clone [modified protobuf](https://github.com/metaworking/protobuf) `https://github.com/metaworking/protobuf.git`
2. Go to protobuf repo dir
3. Run cmd to complie protoc.exe
    ```
    cd <protobuf repo dir>

    call <Microsoft Visual Studio Program File>\VC\Auxiliary\Build\vcvars64.bat
    @REM For example: call "%ProgramFiles%\Microsoft Visual Studio\2022\Community\VC\Auxiliary\Build\vcvars64.bat"
    
    cmake ./cmake -G "NMake Makefiles" -DCMAKE_BUILD_TYPE="Release" -DCMAKE_INSTALL_PREFIX=./ -DBUILD_SHARED_LIBS=OFF -Dprotobuf_BUILD_TESTS=OFF -Dprotobuf_BUILD_CONFORMANCE=OFF -Dprotobuf_BUILD_EXAMPLES=OFF -Dprotobuf_BUILD_PROTOC_BINARIES=ON -Dprotobuf_MSVC_STATIC_RUNTIME=OFF
    
    nmake -nologo install
    ```
4. Copy the `/bin/protoc.exe` binary file in **protobuf repo dir** to `/Source/Protobuf/ThirdParty/bin/` in **ue4-protobuf dir** 