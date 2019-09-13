---
title: 使用 Docker 教學課程將應用程式容器化
description: 在此教學課程中，您將了解如何使用 Docker 來將 .NET Core 應用程式容器化。
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: f0e0fad9bde4c35fb5c5b0b505b9fa8441e432ba
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926309"
---
# <a name="tutorial-containerize-a-net-core-app"></a>教學課程：將 .NET Core 應用程式容器化

本教學課程將教您如何建置包含 .NET Core 應用程式的 Docker 映像。 映像可用來為您的本機開發環境、私人雲端，或公用雲端建立容器。

您將了解：

> [!div class="checklist"]
>
> * 建立及發佈簡單的 .NET Core 應用程式
> * 建立及設定適用於 .NET Core 的 Dockerfile
> * 建置 Docker 映像
> * 建立及執行 Docker 容器

您將了解 .NET Core 應用程式的 Docker 容器建置及部署工作。 「Docker 平台」會使用「Docker 引擎」快速建置應用程式，並將其封裝為「Docker 映像」。 這些映像是以 *Dockerfile* 格式所撰寫，可在分層式容器中部署及執行。

## <a name="prerequisites"></a>必要條件

安裝下列先決條件：

* [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download)\
如果您已安裝 .NET Core，請使用 `dotnet --info` 命令來判斷您使用的 SDK。

* [Docker Community Edition](https://www.docker.com/products/docker-desktop)

* *Dockerfile* 和 .NET Core 範例應用程式的暫存工作資料夾。 在本教學課程中，`docker-working` 名稱會作為工作資料夾使用。

### <a name="use-sdk-version-22"></a>使用 SDK 版本 2.2

如果您使用較新的 SDK (例如 3.0)，請務必強制您的應用程式使用 2.2 SDK。 在您的工作資料夾中建立名為 `global.json` 的檔案，並貼到下列 json 程式碼：

```json
{
  "sdk": {
    "version": "2.2.100"
  }
}
```

儲存此檔案。 檔案的存在將強制 .NET Core 針對從此資料夾及以下資料夾呼叫的所有 `dotnet` 命令使用版本 2.2。

## <a name="create-net-core-app"></a>建立 .NET Core 應用程式

您需要 Docker 容器將執行的 .NET Core 應用程式。 開啟您的終端機，建立工作資料夾 (如果沒有)，並進入該資料夾。 在工作資料夾中執行下列命令，在名為 app 的子目錄中建立新專案：

```console
dotnet new console -o app -n myapp
```

您的資料夾樹狀目錄會如下所示：

```
docker-working
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    └───obj
            myapp.csproj.nuget.cache
            myapp.csproj.nuget.g.props
            myapp.csproj.nuget.g.targets
            project.assets.json
```

`dotnet new` 命令會建立名為 *app* 的新資料夾，並產生 "Hello World" 應用程式。 請進入 *app* 資料夾，然後執行命令 `dotnet run`。 您將會看到下列輸出：

```console
> dotnet run
Hello World!
```

預設範本所建立的應用程式會列印到終端機，然後結束。 針對此教學課程，您將使用無限期執行迴圈的應用程式。 在文字編輯器中開啟 **Program.cs** 檔案。 它目前看起來應該像下列程式碼：

```csharp
using System;

namespace myapp
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

namespace myapp
{
    class Program
    {
        static void Main(string[] args)
        {
            var counter = 0;
            var max = args.Length != 0 ? Convert.ToInt32(args[0]) : -1;
            while(max == -1 || counter < max)
            {
                counter++;
                Console.WriteLine($"Counter: {counter}");
                System.Threading.Tasks.Task.Delay(1000).Wait();
            }
        }
    }
}
```

儲存檔案，然後使用 `dotnet run` 再次測試程式。 請記住此應用程式會無限期執行。 使用取消命令 <kbd>CTRL + C</kbd> 來停止它。 您將會看到下列輸出：

```console
> dotnet run
Counter: 1
Counter: 2
Counter: 3
Counter: 4
^C
```

如果您在命令列上傳遞一個數字給應用程式，它將只會計算到該數量，然後結束。 搭配 `dotnet run -- 5` 試用它以計算到五。

> [!NOTE]
> `--` 之後的任何參數都不會傳遞至 `dotnet run` 命令，而會改為傳遞至您的應用程式。

## <a name="publish-net-core-app"></a>發佈 .NET Core 應用程式

將 .NET Core 應用程式新增至 Docker 映像之前，請先發佈它。 建議您確定容器啟動時，會執行已發佈的應用程式版本。

從工作資料夾中，進入含有範例原始程式碼的 **app** 資料夾，然後執行下列命令：

```console
dotnet publish -c Release
```

此命令會將您的應用程式編譯至 **publish** 資料夾。 從工作資料夾通往 **publish** 資料夾的路徑應該是 `.\app\bin\Release\netcoreapp2.2\publish\`

取得 publish 資料夾的目錄清單，以確認 **myapp.dll** 已建立。 從 **app** 資料夾中，執行下列其中一個命令：

```console
> dir bin\Release\netcoreapp2.2\publish
 Directory of C:\docker-working\app\bin\Release\netcoreapp2.2\publish

04/05/2019  11:00 AM    <DIR>          .
04/05/2019  11:00 AM    <DIR>          ..
04/05/2019  11:00 AM               447 myapp.deps.json
04/05/2019  11:00 AM             4,608 myapp.dll
04/05/2019  11:00 AM               448 myapp.pdb
04/05/2019  11:00 AM               154 myapp.runtimeconfig.json
```

```bash
me@DESKTOP:/docker-working/app$ ls bin/Release/netcoreapp2.2/publish
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
```

## <a name="create-the-dockerfile"></a>建立 Dockerfile

`docker build` 命令會使用 *Dockerfile* 檔案來建立容器映像。 此檔案是名為 *Dockerfile* 且沒有副檔名的純文字檔案。

在您的終端機中，瀏覽至上一層目錄來移至您一開始建立的工作資料夾。 在工作資料夾中建立名為 *Dockerfile* 的檔案，然後在文字編輯器中開啟它。 將下列命令新增為檔案的第一行：

```dockerfile
FROM mcr.microsoft.com/dotnet/core/runtime:2.2
```

`FROM` 命令會指示 Docker 從 **mcr.microsoft.com/dotnet/core/runtime** 存放庫提取標記為 **2.2** 的映像。 確定您所提取的 .NET Core 執行階段符合您 SDK 以其為目標的執行階段。 例如，上一節中所建立的應用程式會使用 .NET Core 2.2 SDK，並建立目標為 .NET Core 2.2 的應用程式。 因此，*Dockerfile* 中所參考的基底映像會以 **2.2** 來標記。

儲存 *Dockerfile* 檔案。 工作資料夾的目錄結構應如下所示。 部分更下層的檔案和資料夾已省略，以節省文章空間：

```
docker-working
│   Dockerfile
│   global.json
│
└───app
    │   myapp.csproj
    │   Program.cs
    │
    ├───bin
    │   └───Release
    │       └───netcoreapp2.2
    │           └───publish
    │                   myapp.deps.json
    │                   myapp.dll
    │                   myapp.pdb
    │                   myapp.runtimeconfig.json
    │
    └───obj
```

從終端機執行下列命令：

```console
docker build -t myimage -f Dockerfile .
```

Docker 將會處理 *Dockerfile* 中的每一行。 `docker build` 命令中的 `.` 會指示 Docker 使用目前的資料夾來尋找 *Dockerfile*。 此命令會建置映像，並建立名為 **myimage** 的本機存放庫以指向該映像。 當此命令完成之後，執行 `docker images` 以查看已安裝的映像清單：

```console
> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
myimage                                 latest              d51bb4452469        2 days ago          314MB
```

請注意，這兩個映像會共用相同的**映像識別碼**值。 此值在這兩個映像之間是一樣的，因為 *Dockerfile* 中的唯一命令會以現有映像上的新映像為依據。 讓我們在 *Dockerfile* 中新增兩個命令。 每個命令都會使用最後一個命令來建立新的映像圖層，其代表 **myimage** 存放庫將指向的映像。

```dockerfile
COPY app/bin/Release/netcoreapp2.2/publish/ app/

ENTRYPOINT ["dotnet", "app/myapp.dll"]
```

`COPY` 命令會指示 Docker，將您電腦上指定的資料夾複製到容器中的資料夾。 在此範例中，會將 **publish** 資料夾複製到容器中名為 **app** 的資料夾。

下一個命令 `ENTRYPOINT` 會指示 Docker 將容器設定為以可執行檔的形式執行。 當容器啟動時，`ENTRYPOINT` 命令就會執行。 當此命令結束時，容器將會自動停止。

從終端機中執行 `docker build -t myimage -f Dockerfile .`，並在該命令完成時，執行 `docker images`。

```console
> docker build -t myimage -f Dockerfile .
Sending build context to Docker daemon  819.7kB
Step 1/3 : FROM mcr.microsoft.com/dotnet/core/runtime:2.2
 ---> d51bb4452469
Step 2/3 : COPY app/bin/Release/netcoreapp2.2/publish/ app/
 ---> a1e98ac62017
Step 3/3 : ENTRYPOINT ["dotnet", "app/myapp.dll"]
 ---> Running in f34da5c18e7c
Removing intermediate container f34da5c18e7c
 ---> ddcc6646461b
Successfully built ddcc6646461b
Successfully tagged myimage:latest

> docker images
REPOSITORY                              TAG                 IMAGE ID            CREATED             SIZE
myimage                                 latest              ddcc6646461b        10 seconds ago      314MB
mcr.microsoft.com/dotnet/core/runtime   2.2                 d51bb4452469        2 days ago          314MB
```

*Dockerfile* 中的每個命令都會產生一個圖層，並建立**映像識別碼**。 最終的**映像識別碼** (您的映像識別碼將會不同) 為 **ddcc6646461b**，接下來您將根據此映像建立容器。

## <a name="create-a-container"></a>建立容器

您現在已有包含應用程式的映像，您可以建立一個容器。 您可以兩種方式建立容器。 首先，建立已停止的新容器。

```console
> docker create myimage
0e8f3c2ca32ce773712a5cca38750f41259a4e54e04bdf0946087e230ad7066c
```

上述的 `docker create` 命令將根據 **myimage** 映像建立容器。 該命令的輸出會顯示已建立容器的**容器識別碼** (您的映像識別碼將會不同)。 若要查看「所有」容器的清單，請使用 `docker ps -a` 命令：

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS        PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   4 seconds ago       Created               boring_matsumoto
```

### <a name="manage-the-container"></a>管理容器

每個容器會被指派隨機的名稱，可供您用來參考該容器執行個體。 例如，已自動建立的容器選擇了名稱 **boring_matsumoto** (您的名稱將會不同)，而該名稱可用來啟動容器。 您會使用 `docker create --name` 參數，利用特定的名稱來覆寫自動名稱。

下列範例會使用 `docker start` 命令來啟動容器，然後使用 `docker ps` 命令只顯示正在執行的容器：

```console
> docker start boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS         PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   7 minutes ago       Up 8 seconds           boring_matsumoto
```

同樣地，`docker stop` 命令將會停止容器。 下列範例會使用 `docker stop` 命令來停止容器，然後使用 `docker ps` 命令顯示沒有任何容器正在執行。

```console
> docker stop boring_matsumoto
boring_matsumoto

> docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS   NAMES
```

### <a name="connect-to-a-container"></a>連線到容器

當容器正在執行之後，您可以連線到它以查看輸出。 使用 `docker start` 和 `docker attach` 命令來啟動容器，並查看輸出資料流。 在此範例中，會使用 <kbd>CTRL + C</kbd> 命令來將執行中的容器中斷連結。 這實際上可能會結束容器中的程序，其將會停止容器。 `--sig-proxy=false` 參數可確保 <kbd>CTRL + C</kbd> 不會停止容器中的流程。

當您從容器中斷連結之後，請重新連結以確認它仍在執行且正在進行計算。

```console
> docker start boring_matsumoto
boring_matsumoto

> docker attach --sig-proxy=false boring_matsumoto
Counter: 7
Counter: 8
Counter: 9
^C

> docker attach --sig-proxy=false boring_matsumoto
Counter: 17
Counter: 18
Counter: 19
^C
```

### <a name="delete-a-container"></a>刪除容器

基於此文章的目的，您不想讓容器什麼都不做而只處於懸置狀態。 刪除您先前建立的容器。 如果容器正在執行，請停止它。

```console
> docker stop boring_matsumoto
```

下列範例會列出所有容器。 它接著會使用 `docker rm` 命令來刪除容器，然後第二次檢查任何執行中的容器。

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS     PORTS   NAMES
0e8f3c2ca32c        myimage             "dotnet app/myapp.dll"   19 minutes ago      Exited             boring_matsumoto

> docker rm boring_matsumoto
boring_matsumoto

> docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS     PORTS    NAMES
```

### <a name="single-run"></a>單一執行

Docker 提供 `docker run` 命令來建立容器，並以單一命令執行。 使用此命令，就不需依序執行 `docker create` 及 `docker start`。 您也可以設定此命令，在容器停止時自動刪除容器。 例如，使用 `docker run -it --rm` 來執行兩個動作，首先，自動使用目前的終端機連線到容器，然後在容器完成時將其移除：

```console
> docker run -it --rm myimage
Counter: 1
Counter: 2
Counter: 3
Counter: 4
Counter: 5
^C
```

搭配 `docker run -it`，則 <kbd>CTRL + C</kbd> 命令將會停止正在容器中執行的程序，接著停止容器。 由於已提供 `--rm` 參數，因此會在程序停止時自動刪除容器。 確認它不存在：

```console
> docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS    PORTS   NAMES
```

### <a name="change-the-entrypoint"></a>變更 ENTRYPOINT

`docker run` 命令也可讓您從 *Dockerfile* 修改 `ENTRYPOINT` 命令並執行其他動作，但只適用於該容器。 例如，使用下列命令來執行 `bash` 或 `cmd.exe`。 視需要編輯命令。

#### <a name="windows"></a>Windows
在此範例中，`ENTRYPOINT` 會變更為 `cmd.exe`。 按下 <kbd>CTRL + C</kbd> 以結束程序並停止容器。

```console
> docker run -it --rm --entrypoint "cmd.exe" myimage

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

#### <a name="linux"></a>Linux

在此範例中，`ENTRYPOINT` 會變更為 `bash`。 執行 `quit` 命令以結束程序並停止容器。

```bash
root@user:~# docker run -it --rm --entrypoint "bash" myimage
root@8515e897c893:/# ls app
myapp.deps.json  myapp.dll  myapp.pdb  myapp.runtimeconfig.json
root@8515e897c893:/# exit
exit
```

## <a name="essential-commands"></a>基本命令

Docker 有許多不同的命令，其中涵蓋您想要使用容器和映像來執行的動作。 這些 Docker 命令對於管理容器而言非常重要：

* [docker build](https://docs.docker.com/engine/reference/commandline/build/)
* [docker run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)

## <a name="clean-up-resources"></a>清除資源

在此教學課程中，您建立了容器與映像。 您可以視需要刪除這些資源。 使用下列命令

01. 列出所有容器

    ```console
    > docker ps -a
    ```

02. 停止正在執行的容器。 `CONTAINER_NAME` 代表自動指派給容器的名稱。

    ```console
    > docker stop CONTAINER_NAME
    ```

03. 刪除容器

    ```console
    > docker rm CONTAINER_NAME
    ```

接下來，在電腦上刪除您不再需要的任何映像。 刪除 *Dockerfile* 所建立的映像，然後刪除 *Dockerfile* 以其為基礎的 .NET Core 映像。 您可以使用**映像識別碼**或**存放庫:標記**格式的字串。

```console
docker rmi myimage:latest
docker rmi mcr.microsoft.com/dotnet/core/runtime:2.2
```

使用 `docker images` 命令來查看已安裝的映像清單。

> [!NOTE]
> 映像檔可能很大。 一般而言，會移除您在測試及開發應用程式時所建立的暫存容器。 如果您打算根據已安裝的執行階段建置其他映像，您通常會使用該執行階段來保存基底映像。

## <a name="next-steps"></a>後續步驟

* [嘗試 ASP.NET Core 微服務教學課程。](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro) \(英文\)
* [檢閱支援容器的 Azure 服務。](https://azure.microsoft.com/overview/containers/)
* [了解 Dockerfile 命令。](https://docs.docker.com/engine/reference/builder/) \(英文\)
* [探索 Visual Studio 的容器工具](/visualstudio/containers/overview)
