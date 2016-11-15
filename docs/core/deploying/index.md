---
title: ".NET Core 應用程式部署"
description: ".NET Core 應用程式部署"
keywords: ".NET、.NET Core、.NET Core 部署"
author: rpetrusha
manager: wpickett
ms.date: 09/08/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: da7a31a0-8072-4f23-82aa-8a19184cb701
translationtype: Human Translation
ms.sourcegitcommit: 663f4102b82512e64ab39d8046c7298a7cf37de7
ms.openlocfilehash: 96eb2cc7ca948b3e372fa1363b1741624d791d27

---

# <a name="net-core-application-deployment"></a>.NET Core 應用程式部署 #

您可以建立兩種類型的 .NET Core 應用程式部署︰ 

- 與 Framework 相依的部署。 正如其名，與 Framework 相依的部署 (FDD) 要仰賴全系統共用的 .NET Core 版本才能存在於目標系統上。 因為 .NET Core 已存在，所以應用程式也可以在 .NET Core 安裝之間攜帶。 您的應用程式僅包含其自有程式碼和 .NET Core 程式庫以外的所有協力廠商相依性。 FDD 包含的 .dll 檔案，可以使用 [dotnet 公用程式](../tools/dotnet.md)從命令列啟動。 例如，`dotnet app.dll` 執行名為 `app` 的應用程式。

- 自封式部署。 不同於 FDD，自封式部署 (SCD) 不仰賴任何共用的元件就能存在於目標系統上。 所有的元件，包括 .NET Core 程式庫和 .NET Core 執行階段，都隨附於應用程式，並與其他 .NET Core 應用程式隔離。 SCD 包含可執行檔 (例如，Windows 平台上 `app` 應用程式的 `app.exe`)，這是重新命名的特定平台 .NET Core 主應用程式版本，以及實際的應用程式 .dll 檔案 (例如 `app.dll`)。

## <a name="frameworkdependent-deployments-fdd"></a>與 Framework 相依的部署 (FDD) ##

在 FDD，您只要部署自己的應用程式和任何協力廠商相依性。 您不必部署 .NET Core，因為您的應用程式會使用存在於目標系統上的 .NET Core 版本。 這是 .NET Core 應用程式的預設部署模型。

### <a name="why-create-a-frameworkdependent-deployment"></a>為何建立與 Framework 相依的部署？ ###

部署 FDD 有許多優點︰

- 您不必事先定義 .NET Core 應用程式執行所在的目標作業系統。 由於不論作業系統為何，.NET Core 對可執行檔和程式庫都使用通用的 PE 檔案格式，所以 .NET Core 可以執行您的應用程式，不理會基礎作業系統。 如需 PE 檔格式的詳細資訊，請參閱 [.NET Assembly File Format](../../standard/assembly-format.md) (.NET 組件檔案格式)。

- 部署套件的大小很小。 您只需要部署您的應用程式及其相依性，不用部署 .NET Core。

- 多個應用程式使用相同的 .NET Core 安裝，這樣可減少主機系統的磁碟空間和記憶體使用量。

另外還有幾個缺點︰

- 只有主機系統安裝了目標的 .NET Core 版本或更新版本，您的應用程式才能執行。

- .NET Core 執行階段和程式庫在未來的版本中可能有所變更，但不會通知您。 只有極其罕見的情況，才可能變更應用程式的行為。

### <a name="deploying-a-frameworkdependent-deployment"></a>部署與 Framework 相依的部署 ###

部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。 以 C# 撰寫的簡單範例會說明此程序。 此範例從命令列使用 [dotnet 公用程式](../tools/dotnet.md)，但您也可以使用開發環境，例如 Visual Studio 或 Visual Studio Code，來編譯、測試及發行範例。

1. 建立專案目錄，並從命令列輸入 [dotnet new](../tools/dotnet-new.md) 來建立新的 C# 主控台專案。

2. 在編輯器中開啟 `Program.cs` 檔案，並以下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，然後顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else
              {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. 執行 [dotnet restore](../tools/dotnet-restore.md) 命令還原專案中指定的相依性。

4. 使用 [dotnet build](../tools/dotnet-build.md) 命令建立應用程式的偵錯組置。

5. 偵錯並測試程式之後，您可以使用 `dotnet publish -f netcoreapp1.0 -c release` 命令建立要隨應用程式一起部署的檔案。 這會建立應用程式的發行 (而非偵錯) 版本。

   產生的檔案會放在名為 `publish` 的目錄中，位在您專案的 `.\bin\release\netcoreapp1.0` 子目錄的子目錄中。

6. 隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 檔案主要用於偵錯例外狀況，您可以選擇應用程式檔案不封裝它。

整組應用程式檔案可以任何您想要的方式部署。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 zip 檔案中，或與您選擇的任何安裝封裝一起部署。

除了應用程式二進位檔外，安裝程式也應該配套共用的 Framework 安裝程式，或勾選為必要條件當成應用程式安裝的一部分。  共用 Framework 安裝需要系統管理員/根目錄存取權，因為它要通行全機器。

### <a name="deploying-a-frameworkdependent-deployment-with-thirdparty-dependencies"></a>部署具有協力廠商相依性的 Framework 相依部署 ###

部署具有一或多個協力廠商相依性的 Framework 相依部署，包含三個額外的步驟，然後才能執行 `dotnet restore` 命令︰

1. 將任何協力廠商程式庫參考加入您 `project.json` 檔案的 `dependencies` 區段。 下列 `dependencies` 區段會使用 Json.NET 當成協力廠商程式庫。

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": {
        "type": "platform",
        "version": "1.0.0"
      },
      "Newtonsoft.Json": "9.0.1"
    },
    ```

2. 如果尚未如此做，請下載包含協力廠商相依性的 NuGet 封裝。 若要下載封裝，請在加入相依性後執行 `dotnet restore` 命令。 因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。

請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。 例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。 如果協力廠商相依性本身依賴於原生程式碼，就可能發生這種情況。 Kestrel 伺服器即是一個好例子。 當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個 [執行階段識別碼 (RID)](../rid-catalog.md#what-are-rids) 資料夾 (存在其 NuGet 封裝中)。

## <a name="selfcontained-deployments-scd"></a>自封式部署 (SCD) ##

針對自封式部署，您不僅要部署自己的應用程式和所有協力廠商相依性，還要部署建置應用程式所用的 .NET Core 版本。 不過，建立 SCD 不包含各種平台上的 [.NET Core 原生相依性](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md)本身在 (例如，macOS 上的 OpenSSL)，所以您要先安裝這些，才能執行應用程式。 

### <a name="why-deploy-a-selfcontained-deployment"></a>為什麼要部署自封式部署？ ###

部署自封式部署有兩大優點︰

- 您可以獨家控制隨應用程式部署的 .NET Core 版本。 只有您可以提供 .NET Core 服務。

- 您可以保證目標系統能執行您的 .NET Core 應用程式，因為您提供的是它可以執行的 .NET Core 版本。

它也有一些缺點︰

- 因為 .NET Core 包含在您的部署套件中，所以您必須事先選取部署套件建置所在的目標平台。

- 您的部署套件的大小相當大，因為您必須包含 .NET Core 以及應用程式及其協力廠商相依性。

- 將多個自封式 .NET Core 應用程式部署到系統，會消耗大量的磁碟空間，因為每個應用程式都會重複 .NET Core 檔案。

### <a name="a-namesimpleselfa-deploying-a-simple-selfcontained-deployment"></a>進行簡單的自封式部署 ###

部署無任何協力廠商相依性的自封式部署，涉及建立專案、修改 project.json 檔案、建置、測試以及發行應用程式。  以 C# 撰寫的簡單範例會說明此程序。 此範例從命令列使用 `dotnet` 公用程式，但您也可以使用開發環境，例如 Visual Studio 或 Visual Studio Code，來編譯、測試及發行範例。

1. 建立專案目錄，並從命令列輸入 `dotnet new` 來建立新的 C# 主控台專案。

2. 在編輯器中開啟 `Program.cs` 檔案，並以下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，然後顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

    ```cs
    using System;
    using System.Text.RegularExpressions;

    namespace Applications.ConsoleApps
    {
        public class ConsoleParser
        {
            public static void Main()
            {
                 Console.WriteLine("Enter any text, followed by <Enter>:\n");
                 String s = Console.ReadLine();
                 ShowWords(s);
                 Console.Write("\nPress any key to continue... ");
                 Console.ReadKey();
          }

          private static void ShowWords(String s)
          {
              String pattern = @"\w+";
              var matches = Regex.Matches(s, pattern);
              if (matches.Count == 0)
                  Console.WriteLine("\nNo words were identified in your input.");
              else {
                  Console.WriteLine("\nThere are {0} words in your string:", matches.Count);
                  for (int ctr = 0; ctr < matches.Count; ctr++)
                      Console.WriteLine("   #{0,2}: '{1}' at position {2}", ctr,
                                        matches[ctr].Value, matches[ctr].Index);
              }
          }
      }
    }
    ```

3. 開啟 `frameworks` 區段的 `project.json` 檔案，移除下行︰

   ```json
   "type": "platform",
   ```
修改它後，Framework 區段應會出現，如下所示︰

    ```json
    "frameworks": {
      "netcoreapp1.0": {
        "dependencies": {
          "Microsoft.NETCore.App": {
             "version": "1.0.0"
          }
        }
      }
    }
    ```
移除 `"type": "platform"` 屬性指出 Framework 已提供為應用程式的一組本機元件，而非全系統的平台封裝。

4. 在定義應用程式目標平台的 `project.json` 檔案中建立 `runtimes` 區段，並指定每個目標平台的執行階段識別碼。 如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。 例如，下列 `runtimes` 區段指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.10 作業系統上執行。

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
請注意，您也需要加入逗號來分隔 `runtimes` 區段與上一個區段。
本節稍後會提供完整的範例 `project.json` 檔。

6. 執行 `dotnet restore` 命令還原專案中指定的相依性。

7. 使用 `dotnet build` 命令在每個目標平台上建立應用程式的偵錯組建。 除非您指定想要建置的執行階段識別碼，否則 `dotnet build` 命令只會建立目前系統的執行階段識別碼。 您可以使用下列命令為兩個目標平台建置應用程式︰

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```
針對每個平台的應用程式偵錯組建位於專案的 `.\bin\Debug\netcoreapp1.0\<runtime_identifier>` 子目錄。

8. 偵錯並測試完程式之後，您可以對兩個目標平台使用 `dotnet publish` 命令，建立針對每個目標平台要與應用程式一起部署的檔案，如下所示︰

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
這會建立每個目標平台的應用程式發行 (而非偵錯) 版本。 產生的檔案會放在名為 `publish` 的子目錄中，位在您專案的 `.\bin\release\netcoreapp1.0\<runtime_identifier>` 子目錄的子目錄中。 請注意，每個子目錄都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。

9. 隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 檔案主要用於偵錯例外狀況，您可以選擇應用程式檔案不封裝它。

您可以任何想要的方式部署已發行的檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 zip 檔案中，或與您選擇的任何安裝封裝一起部署。 

下面是此專案的完整 `project.json` 檔案。

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {},
  "frameworks": {
    "netcoreapp1.0": {
      "dependencies": {
        "Microsoft.NETCore.App": {
          "version": "1.0.0"
        }
      }
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

### <a name="deploying-a-selfcontained-deployment-with-thirdparty-dependencies"></a>部署具有協力廠商相依性的自封式部署 ###

部署具有一或多個協力廠商相依性的自封式部署，涉及新增協力廠商相依性︰

1. 將任何協力廠商程式庫參考加入您 `project.json` 檔案的 `dependencies` 區段。 下列 `dependencies` 區段會使用 Json.NET 當成協力廠商程式庫。

    ```json
    "dependencies": {
      "Microsoft.NETCore.App": "1.0.0",
      "Newtonsoft.Json": "9.0.1"
    },
    ```
2. 如果尚未如此做，請將包含協力廠商相依性的 NuGet 封裝下載至您的系統。 請在加入相依性後執行 `dotnet restore` 命令，讓應用程式取得相依性。 因為相依性是在發行時於本機 NuGet 快取外解析，所以必須能在系統中取得。

下面是此專案的完整 project.json 檔案：

```json
{
  "version": "1.0.0-*",
  "buildOptions": {
    "debugType": "portable",
    "emitEntryPoint": true
  },
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0",
    "Newtonsoft.Json": "9.0.1"
  },
  "frameworks": {
    "netcoreapp1.0": {
    }
  },
  "runtimes": {
    "win10-x64": {},
    "osx.10.10-x64": {}
  }
}
```

當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。 協力廠商程式庫尚未出現在應用程式執行所在的系統上。

請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。 這類似在與 Framework 相依的部署中有帶原生相依性的協力廠商相依性。 

### <a name="deploying-a-selfcontained-deployment-with-a-smaller-footprint"></a>部署使用量較小的自封式部署 ###

如果目標系統上無法取得足夠的儲存空間，您可以排除某些系統元件，以減少應用程式的整體使用量。 若要這樣做，您可以在 project.json 檔案中明確定義應用程式包含的 .NET Core 元件。

若要建立使用量較小的自封式部署，請從建立自封式部署的前兩個步驟開始。 一旦執行了 `dotnet new` 命令，並將 C# 原始程式碼加入到您的應用程式中，請執行下列動作︰

1. 開啟 `project.json` 檔案，並以下列內容取代 `frameworks` 區段：

    ```json
    "frameworks": {
      "netstandard1.6": { }
    }
    ```
這會執行兩項作業︰

    * 它會指出，而不是使用整個 `netcoreapp1.0` Framework，哪些包括 .NET Core CLR、.NET Core 程式庫和幾個其他系統元件，而我們的應用程式只使用 .NET 標準庫。

    * 藉由移除 `"type": "platform"` 屬性，指出 Framework 已提供為應用程式的一組本機元件，而非全系統的平台封裝。

2. 以下列內容取代 `dependencies` 區段：

    ```json
    "dependencies": {
      "NETStandard.Library": "1.6.0",
      "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
      "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
    },
    ```
   這會定義我們應用程式所使用的系統元件。 與我們的應用程式一起封裝的系統元件，包括 .NET 標準程式庫、.NET Core 執行階段和 .NET Core 主應用程式。 這會產生使用量較小的自封式部署。

3. 如您在[部署簡單的自封式部署](#simpleSelf)範例中所做的那樣，在定義應用程式目標平台的 `project.json` 檔案中建立 `runtimes` 區段，並指定每個目標平台的執行階段識別碼。 如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。 例如，下列 `runtimes` 區段指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.10 作業系統上執行。

    ```json
        "runtimes": {
          "win10-x64": {},
          "osx.10.10-x64": {}
        }
    ```
請注意，您也需要加入逗號來分隔 `runtimes` 區段與上一個區段。
本節稍後會提供完整的範例 `project.json` 檔。

4. 執行 `dotnet restore` 命令還原專案中指定的相依性。

5. 使用 `dotnet build` 命令在每個目標平台上建立應用程式的偵錯組建。 除非您指定想要建置的執行階段識別碼，否則 `dotnet build` 命令只會建立目前系統的執行階段識別碼。 您可以使用下列命令為兩個目標平台建置應用程式︰

    ```console
    dotnet build -r win10-x64
    dotnet build -r osx.10.10-x64
    ```

6. 偵錯並測試完程式之後，您可以對兩個目標平台使用 `dotnet publish` 命令，建立針對每個目標平台要與應用程式一起部署的檔案，如下所示︰

   ```console
   dotnet publish -c release -r win10-x64
   dotnet publish -c release -r osx.10.10-x64
   ```
這會建立每個目標平台的應用程式發行 (而非偵錯) 版本。 產生的檔案會放在名為 `publish` 的子目錄中，位在您專案的 `.\bin\release\netstandard1.6\<runtime_identifier>` 子目錄的子目錄中。 請注意，每個子目錄都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。

7. 隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 檔案主要用於偵錯例外狀況，您可以選擇應用程式檔案不封裝它。

您可以任何想要的方式部署已發行的檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 zip 檔案中，或與您選擇的任何安裝封裝一起部署。 

下面是此專案的完整 `project.json` 檔案。

```json
   {
     "version": "1.0.0-*",
     "buildOptions": {
       "debugType": "portable",
       "emitEntryPoint": true
     },
     "dependencies": {
       "NETStandard.Library": "1.6.0",
       "Microsoft.NETCore.Runtime.CoreCLR": "1.0.2",
       "Microsoft.NETCore.DotNetHostPolicy":  "1.0.1"
     },
     "frameworks": {
       "netstandard1.6": { }
     },
     "runtimes": {
       "win10-x64": {},
       "osx.10.10-x64": {}
     }
   }
```



<!--HONumber=Nov16_HO3-->


