---
title: 使用 Docker 教學課程將應用程式容器化
description: 在本教學課程中，您將瞭解如何使用 Docker 容器化 .NET Core 應用程式。
ms.date: 04/27/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: c5e6648539af45f3ce615bfc183e6f95a62b085a
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200024"
---
# <a name="tutorial-containerize-a-net-core-app"></a>教學課程：容器化 .NET Core 應用程式

在本教學課程中，您將瞭解如何使用 Docker 容器化 .NET Core 應用程式。 容器有許多功能和優點，例如成為不可變的基礎結構、提供可移植的架構，以及啟用擴充性。 映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。

在本教學課程中，您：

> [!div class="checklist"]
>
> - 建立及發佈簡單的 .NET Core 應用程式
> - 建立及設定適用於 .NET Core 的 Dockerfile
> - 建置 Docker 映像
> - 建立及執行 Docker 容器

您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。 *Docker 平臺*會使用*docker 引擎*來快速建立應用程式，並將其封裝為*Docker 映射*。 這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。

> [!NOTE]
> 本教學課程**不適**用於 ASP.NET Core 應用程式。 如果您使用 ASP.NET Core，請參閱[瞭解如何容器化 ASP.NET Core 應用程式](/aspnet/core/host-and-deploy/docker/building-net-docker-images)教學課程。

## <a name="prerequisites"></a>先決條件

安裝下列先決條件：

- [.NET Core 3.1 SDK](https://dotnet.microsoft.com/download)\
如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。
- [Docker Community Edition](https://www.docker.com/products/docker-desktop)
- *Dockerfile* 和 .NET Core 範例應用程式的暫存工作資料夾。 在本教學課程中，會使用*docker-作用*中的名稱做為工作資料夾。

## <a name="create-net-core-app"></a>建立 .NET Core 應用程式

您需要 Docker 容器將執行的 .NET Core 應用程式。 開啟您的終端機，建立工作資料夾 (如果沒有)，並進入該資料夾。 在工作資料夾中，執行下列命令以在名為*app*的子目錄中建立新的專案：

```dotnetcli
dotnet new console -o App -n NetCore.Docker
```

您的資料夾樹狀目錄會如下所示：

```
docker-working
    └──App
        ├──NetCore.Docker.csproj
        ├──Program.cs
        └──obj
            ├──NetCore.Docker.csproj.nuget.dgspec.json
            ├──NetCore.Docker.csproj.nuget.g.props
            ├──NetCore.Docker.csproj.nuget.g.targets
            ├──project.assets.json
            └──project.nuget.cache
```

此`dotnet new`命令會建立名為*App*的新資料夾，並產生 "Hello World" 主控台應用程式。 從您的終端機會話變更目錄，並流覽至*應用程式*資料夾。 使用`dotnet run`命令來啟動應用程式。 應用程式將會執行，並`Hello World!`在命令下方列印：

```dotnetcli
dotnet run
Hello World!
```

預設範本會建立會列印到終端機的應用程式，然後立即終止。 針對此教學課程，您將使用無限期執行迴圈的應用程式。 在文字編輯器中開啟 *Program.cs* 檔案。

> [!TIP]
> 如果您使用的是 Visual Studio Code，請從先前的終端機會話輸入下列命令：
>
> ```
> code .
> ```
>
> 這會在 Visual Studio Code 中開啟包含專案的*應用程式*資料夾。

*Program.cs*看起來應該像下列 c # 程式碼：

```csharp
using System;

namespace NetCore.Docker
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

使用下列每秒計算數字的程式碼來取代檔案：

```csharp
using System;
using System.Threading.Tasks;

namespace NetCore.Docker
{
    class Program
    {
        static async Task Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while (max == -1 || counter < max)
            {
                Console.WriteLine($"Counter: {++counter}");
                await Task.Delay(1000);
            }
        }
    }
}
```

儲存檔案，然後使用 `dotnet run` 再次測試程式。 請記住此應用程式會無限期執行。 使用 [取消] 命令<kbd>Ctrl + C</kbd>來停止它。 以下是範例輸出：

```dotnetcli
dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。 搭配 `dotnet run -- 5` 試用它以計算到五。

> [!IMPORTANT]
> `--` 之後的任何參數都不會傳遞至 `dotnet run` 命令，而會改為傳遞至您的應用程式。

## <a name="publish-net-core-app"></a>發佈 .NET Core 應用程式

將 .NET Core 應用程式新增至 Docker 映射之前，必須先將它發佈。 最好讓容器執行應用程式的已發佈版本。 若要發佈應用程式，請執行下列命令：

```dotnetcli
dotnet publish -c Release
```

此命令會將您的應用程式編譯至 *publish* 資料夾。 從工作資料夾通往 *publish* 資料夾的路徑應該是 `.\App\bin\Release\netcoreapp3.1\publish\`

#### <a name="windows"></a>[Windows](#tab/windows)

從*應用程式*資料夾中，取得 [發行] 資料夾的目錄清單，以確認已建立*NetCore*檔案。

```powershell
dir .\bin\Release\netcoreapp3.1\publish\

    Directory: C:\Users\dapine\App\bin\Release\netcoreapp3.1\publish

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        4/27/2020   8:27 AM            434 NetCore.Docker.deps.json
-a----        4/27/2020   8:27 AM           6144 NetCore.Docker.dll
-a----        4/27/2020   8:27 AM         171520 NetCore.Docker.exe
-a----        4/27/2020   8:27 AM            860 NetCore.Docker.pdb
-a----        4/27/2020   8:27 AM            154 NetCore.Docker.runtimeconfig.json
```

#### <a name="linux"></a>[Linux](#tab/linux)

使用`ls`命令來取得目錄清單，並確認已建立*NetCore*檔案。

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp3.1/publish
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
```

---

## <a name="create-the-dockerfile"></a>建立 Dockerfile

`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。 此檔案是名為*Dockerfile*的文字檔，沒有副檔名。

在包含 *.csproj*的目錄中建立名為*Dockerfile*的檔案，並在文字編輯器中開啟它。 本教學課程將使用 ASP.NET Core 執行時間映射（其中包含 .NET Core 執行時間映射），並對應至 .NET Core 主控台應用程式。

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
```

> [!NOTE]
> 這裡會刻意使用 ASP.NET Core 執行時間映射，雖然`mcr.microsoft.com/dotnet/core/runtime:3.1`映射可能已經使用過了。

`FROM`關鍵字需要完整的 Docker 容器映射名稱。 Microsoft Container Registry （MCR，mcr.microsoft.com）是 Docker Hub 的聯合，可裝載可公開存取的容器。 `dotnet/core`區段是容器存放庫，其中的`aspnet`區段是容器映射名稱。 影像會標記為`3.1`，用於版本控制。 因此， `mcr.microsoft.com/dotnet/core/aspnet:3.1`是 .net Core 3.1 執行時間。 請確定您已提取符合 SDK 目標執行時間的執行階段版本。 例如，在上一節中建立的應用程式會使用 .NET Core 3.1 SDK，而*Dockerfile*中所參考的基底映射會加上**3.1**。

儲存 *Dockerfile* 檔案。 工作資料夾的目錄結構應如下所示。 已省略一些較深層的檔案和資料夾，以節省文章中的空間：

```
docker-working
    └──App
        ├──Dockerfile
        ├──NetCore.Docker.csproj
        ├──Program.cs
        ├──bin
        │   └──Release
        │       └──netcoreapp3.1
        │           └──publish
        │               ├──NetCore.Docker.deps.json
        │               ├──NetCore.Docker.exe
        │               ├──NetCore.Docker.dll
        │               ├──NetCore.Docker.pdb
        │               └──NetCore.Docker.runtimeconfig.json
        └──obj
            └──...
```

從終端機執行下列命令：

```Docker
docker build -t counter-image -f Dockerfile .
```

Docker 將會處理 *Dockerfile* 中的每一行。 命令中的`.`會指示 Docker 使用目前的資料夾來尋找 Dockerfile。 *Dockerfile* `docker build` 此命令會建立映射，並建立名為**counter 映射**的本機存放庫，以指向該映射。 當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：

```Docker
docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              e6780479db63        4 days ago          190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

請注意，這兩個映像會共用相同的**映像識別碼**值。 此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。 讓我們在*Dockerfile*中新增三個命令。 每個命令都會使用最後一個命令來建立新的映射圖層，其代表**計數器映射**存放庫進入點。

```dockerfile
COPY bin/Release/netcoreapp3.1/publish/ App/
WORKDIR /App
ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
```

`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。 在此範例中，會將*publish*資料夾複製到容器中名為*App*的資料夾。

`WORKDIR`命令會將容器內的**目前目錄**變更為*應用程式*。

下一個命令 `ENTRYPOINT` 會指示 Docker 將容器設定為以可執行檔的形式執行。 當容器啟動時，`ENTRYPOINT` 命令就會執行。 當此命令結束時，容器將會自動停止。

從終端機中執行 `docker build -t counter-image -f Dockerfile .`，並在該命令完成時，執行 `docker images`。

```Docker
docker build -t counter-image -f Dockerfile .
Sending build context to Docker daemon  1.117MB
Step 1/4 : FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
 ---> e6780479db63
Step 2/4 : COPY bin/Release/netcoreapp3.1/publish/ App/
 ---> d1732740eed2
Step 3/4 : WORKDIR /App
 ---> Running in b1701a42f3ff
Removing intermediate container b1701a42f3ff
 ---> 919aab5b95e3
Step 4/4 : ENTRYPOINT ["dotnet", "NetCore.Docker.dll"]
 ---> Running in c12aebd26ced
Removing intermediate container c12aebd26ced
 ---> cd11c3df9b19
Successfully built cd11c3df9b19
Successfully tagged counter-image:latest

docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
counter-image                           latest              cd11c3df9b19        41 seconds ago      190MB
mcr.microsoft.com/dotnet/core/aspnet    3.1                 e6780479db63        4 days ago          190MB
```

*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。 最終的**映射識別碼**（您的會不同）是**cd11c3df9b19** ，接下來您將根據此映射建立容器。

## <a name="create-a-container"></a>建立容器

您現在已有包含應用程式的映像，您可以建立一個容器。 您可以兩種方式建立容器。 首先，建立已停止的新容器。

```Docker
docker create --name core-counter counter-image
0f281cb3af994fba5d962cc7d482828484ea14ead6bfe386a35e5088c0058851
```

上述`docker create`命令會根據**計數器映射**映射來建立容器。 該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。 若要查看「所有」** 容器的清單，請使用 `docker ps -a` 命令：

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED           STATUS     PORTS    NAMES
0f281cb3af99    counter-image    "dotnet NetCore.Dock…"    40 seconds ago    Created             core-counter
```

### <a name="manage-the-container"></a>管理容器

容器是使用特定名稱`core-counter`建立的，此名稱可用來管理容器。 下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：

```Docker
docker start core-counter
core-counter

docker ps
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS          PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    2 minutes ago    Up 11 seconds            core-counter
```

同樣地，`docker stop` 命令將會停止容器。 下列範例會使用`docker stop`命令來停止容器，然後使用`docker ps`命令來顯示沒有容器正在執行：

```Docker
docker stop core-counter
core-counter

docker ps
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="connect-to-a-container"></a>連線到容器

當容器正在執行之後，您可以連線到它以查看輸出。 使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。 在此範例中，會使用<kbd>Ctrl + C</kbd>鍵，從執行中的容器卸離。 除非另有指定，否則此按鍵會結束容器中的進程，這會停止容器。 `--sig-proxy=false`參數可確保<kbd>Ctrl + C</kbd>不會停止容器中的進程。

當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。

```Docker
docker start core-counter
core-counter

docker attach --sig-proxy=false core-counter
Counter: 7
Counter: 8
Counter: 9
^C

docker attach --sig-proxy=false core-counter
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>刪除容器

基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。 刪除您先前建立的容器。 如果容器正在執行，請停止它。

```Docker
docker stop core-counter
```

下列範例會列出所有容器。 它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。

```Docker
docker ps -a
CONTAINER ID    IMAGE            COMMAND                   CREATED          STATUS                        PORTS    NAMES
2f6424a7ddce    counter-image    "dotnet NetCore.Dock…"    7 minutes ago    Exited (143) 20 seconds ago            core-counter

docker rm core-counter
core-counter

docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="single-run"></a>單一執行

Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。 使用此命令，就不需依序執行 `docker create` 及 `docker start`。 您也可以設定此命令，在容器停止時自動刪除容器。 例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：

```Docker
docker run -it --rm counter-image
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

容器也會將參數傳遞至 .NET Core 應用程式的執行。 指示 .NET Core 應用程式只計算3個階段。

```Docker
docker run -it --rm counter-image 3
Counter: 1
Counter: 2
Counter: 3
```

使用`docker run -it`， <kbd>Ctrl + C</kbd>命令會停止在容器中執行的進程，進而停止容器。 由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。 確認它不存在：

```Docker
docker ps -a
CONTAINER ID    IMAGE    COMMAND    CREATED    STATUS    PORTS    NAMES
```

### <a name="change-the-entrypoint"></a>變更 ENTRYPOINT

`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。 例如，使用下列命令來執行 `bash` 或 `cmd.exe`。 視需要編輯命令。

#### <a name="windows"></a>[Windows](#tab/windows)

在此範例中，`ENTRYPOINT` 會變更為 `cmd.exe`。 <kbd>Ctrl + C</kbd>已按下以結束進程並停止容器。

```Docker
docker run -it --rm --entrypoint "cmd.exe" counter-image

Microsoft Windows [Version 10.0.17763.379]
(c) 2018 Microsoft Corporation. All rights reserved.

C:\>dir
 Volume in drive C has no label.
 Volume Serial Number is 3005-1E84

 Directory of C:\

04/09/2019  08:46 AM    <DIR>          app
03/07/2019  10:25 AM             5,510 License.txt
04/02/2019  01:35 PM    <DIR>          Program Files
04/09/2019  01:06 PM    <DIR>          Users
04/02/2019  01:35 PM    <DIR>          Windows
               1 File(s)          5,510 bytes
               4 Dir(s)  21,246,517,248 bytes free

C:\>^C
```

#### <a name="linux"></a>[Linux](#tab/linux)

在此範例中，`ENTRYPOINT` 會變更為 `bash`。 執行 `exit` 命令以結束程序並停止容器。

```bash
docker run -it --rm --entrypoint "bash" counter-image
root@b735b9799abf:/App# ls
NetCore.Docker.deps.json  NetCore.Docker.dll  NetCore.Docker.exe  NetCore.Docker.pdb  NetCore.Docker.runtimeconfig.json
root@b735b9799abf:/App# dotnet NetCore.Docker.dll 3
Counter: 1
Counter: 2
Counter: 3
root@b735b9799abf:/App# exit
exit
```

---

## <a name="essential-commands"></a>基本命令

Docker 有許多不同的命令，可建立、管理及與容器和映射進行互動。 這些 Docker 命令對於管理容器而言非常重要：

- [docker build](https://docs.docker.com/engine/reference/commandline/build/)
- [docker run](https://docs.docker.com/engine/reference/commandline/run/)
- [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
- [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
- [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
- [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
- [docker 映射](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>清除資源

在本教學課程中，您已建立容器和映射。 您可以視需要刪除這些資源。 使用下列命令

01. 列出所有容器

    ```Docker
    docker ps -a
    ```

02. 停止依其名稱執行的容器。

    ```Docker
    docker stop counter-image
    ```

03. 刪除容器

    ```Docker
    docker rm counter-image
    ```

接下來，在電腦上刪除您不再需要的任何映像。 刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。 您可以使用**映像識別碼**或**存放庫:標記**格式的字串。

```Docker
docker rmi counter-image:latest
docker rmi mcr.microsoft.com/dotnet/core/aspnet:3.1
```

使用 `docker images` 命令來查看已安裝的映像清單。

> [!TIP]
> 映像檔可能很大。 一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。 如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。

## <a name="next-steps"></a>後續步驟

- [了解如何將 ASP.NET Core 應用程式容器化。](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
- [嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)
- [檢閱支援容器的 Azure 服務。](https://azure.microsoft.com/overview/containers/)
- [了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)
- [探索 Visual Studio 的容器工具](/visualstudio/containers/overview)
