> [!NOTE]
> 從 .NET Core 2.0 SDK 開始，您不需要執行 [`dotnet restore`](~/docs/core/tools/dotnet-restore.md)，因為所有需要進行還原的命令 (例如 `dotnet new`、`dotnet build` 和 `dotnet run`) 都會以隱含方式執行它。
> 它在執行明確還原有意義的某些情況下仍然是有效的命令，例如 [Azure DevOps Services 中的持續整合組建](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core)，或在需要明確控制還原進行時間的建置系統中。