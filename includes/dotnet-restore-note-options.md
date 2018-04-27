> [!NOTE]
> 從 .NET Core 2.0 開始，您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因為它是以隱含方式由需要進行還原的所有命令執行，例如 `dotnet build` 和 `dotnet run`。 它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Visual Studio Team Services 中的持續整合組建](/vsts/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。
>
> 此命令也支援以完整形式傳入的 `dotnet restore` 選項 (例如 `--source`)。 不支援簡短形式選項，例如 `-s`。