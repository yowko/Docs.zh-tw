---
title: "使用 Visual Studio 部署 .NET Core 應用程式"
description: "了解使用 Visual Studio 的 .NET Core 應用程式部署"
keywords: ".NET、.NET Core、.NET Core 部署"
author: rpetrusha
ms.author: ronpet
ms.date: 04/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 01049a21-fd50-4419-9ab2-0e4a2e091050
ms.workload: dotnetcore
ms.openlocfilehash: a2706aecb80f079e6e735310b09c1062a6953901
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="deploying-net-core-apps-with-visual-studio"></a>使用 Visual Studio 部署 .NET Core 應用程式

您可以將 .NET Core 應用程式部署為「與 Framework 相依的部署」，其中包含您的應用程式二進位檔，但取決於目標系統上是否有 .NET Core 存在，也可以部署為「自封式部署」，其中包含您的應用程式和 .NET Core 二進位檔。 如需 .NET Core 應用程式部署的概觀，請參閱 [.NET Core 應用程式部署](index.md)。

下列各節顯示如何使用 Microsoft Visual Studio 來建立下列類型的部署：

- 與 Framework 相依的部署
- 有協力廠商相依性的 Framework 相依部署
- 自封式部署
- 有協力廠商相依性的自封式部署

如需使用 Visual Studio 來開發 .NET Core 應用程式的資訊，請參閱 [Windows 上 .NET Core 的必要條件](../windows-prerequisites.md#prerequisites-with-visual-studio-2017)。

## <a name="framework-dependent-deployment"></a>與 Framework 相依的部署

部署無任何協力廠商相依性的 Framework 相依部署，只涉及建置、測試和發行應用程式。 以 C# 撰寫的簡單範例會說明此程序。  

1. 建立專案。

   選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [已安裝] 專案類型窗格中的 [.NET Core]，然後選取中央窗格中的 [Console App (.NET Core)] (主控台應用程式 (.NET Core) 範本。 在 [名稱] 文字方塊中輸入專案名稱，例如 "FDD"。 選取 [確定] 按鈕。

1. 新增應用程式的原始程式碼。

   在編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，並顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. 建立應用程式的偵錯組建。

   選取 [組建]  >  [組建方案]。 您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。

1. 部署應用程式。

   在您偵錯並測試程式之後，請建立要隨應用程式一起部署的檔案。 若要從 Visual Studio 發行，請執行下列作業：

      1. 在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。

      1. 以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。

      1. 在 [發行]索引標籤中，選取 [發行]。 Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。

      1. [發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。 設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。

   產生的檔案會放在名為 `PublishOutput` 的目錄中，而該目錄位於您專案之 *.\bin\release* 子目錄的子目錄中。

隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 該檔案主要是用於例外狀況偵錯。 您可以選擇不與您的應用程式檔案一起封裝它。 不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。

以任何您想要的方式，部署整組應用程式檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。 安裝之後，使用者可以使用 `dotnet` 命令並提供應用程式的檔名 (例如，`dotnet fdd.dll`)，來執行您的應用程式。

除了應用程式二進位檔之外，安裝程式也應該配套共用的 Framework 安裝程式，，或勾選為必要條件當成應用程式安裝的一部分。  共用 Framework 安裝需要系統管理員/根目錄存取權，因為它要通行全機器。

## <a name="framework-dependent-deployment-with-third-party-dependencies"></a>有協力廠商相依性的 Framework 相依部署

部署具有一或多個協力廠商相依性的 Framework 相依部署時，需要任何相依性都可供專案使用。 在組建您的應用程式之前，需要執行下列其他步驟：

1. 使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。 若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。

1. 確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。 [已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。 如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。 選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。

1. 如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的套件] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案中。

請注意，具有協力廠商相依性的 Framework 相依部署，可攜性只與其協力廠商相依性一致。 例如，如果協力廠商程式庫只支援 macOS，則應用程式就無法攜至 Windows 系統。 如果協力廠商相依性本身依賴於原生程式碼，就會發生這種情況。 其中一個絶佳範例是 [Kestrel 伺服器](http://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)，它需要對 [libuv](https://github.com/libuv/libuv) 的原生相依性。 當具有這類協力廠商相依性的應用程式建立了 FDD 時，已發行輸出就會包含原生相依性支援的每個[執行階段識別碼 (RID)](../rid-catalog.md) 資料夾 (存在於其 NuGet 套件中)。

## <a name="simpleSelf"></a> 沒有協力廠商相依性的自封式部署

部署無任何協力廠商相依性的自封式部署，涉及建立專案、修改 *csproj* 檔案、組建、測試以及發行應用程式。 以 C# 撰寫的簡單範例會說明此程序。 

1. 建立專案。

   選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [已安裝] 專案類型窗格中的 [.NET Core]，然後選取中央窗格中的 [Console App (.NET Core)] (主控台應用程式 (.NET Core)) 範本。 在 [名稱] 文字方塊中輸入專案名稱 (例如 "SCD")，然後選取 [確定] 按鈕。

1. 新增應用程式的原始程式碼。

   在您的編輯器中開啟 *Program.cs* 檔案，並以下列程式碼取代自動產生的程式碼。 它會提示使用者輸入文字，並顯示使用者輸入的個別文字。 它會使用規則運算式 `\w+` 分隔輸入文字中的字詞。

   [!code-csharp[deployment#1](../../../samples/snippets/core/deploying/deployment-example.cs)]

1. 定義您應用程式目標的平台。

   1. 以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [編輯 SCD.csproj]。

   1. 在定義應用程式目標平台之 *csproj* 檔案的 `<PropertyGroup>` 區段中建立 `<RuntimeIdentifiers>` 標記，並指定每個目標平台的執行階段識別碼 (RID)。 請注意，您也必須加上分號來分隔 RID。 如需執行階段識別碼清單，請參閱 [Runtime IDentifier catalog](../rid-catalog.md)。 

   例如，下列範例指出應用程式在 64 位元 Windows 10 作業系統和 64 位元 OS X 版本 10.11 作業系統上執行。

```xml
<PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
</PropertyGroup>
```
   請注意，`<RuntimeIdentifiers>` 項目可以移至您 *csproj* 檔案中的任何 `<PropertyGroup>`。 本節稍後會提供完整的 *csproj* 檔案範例。

1. 建立應用程式的偵錯組建。

   選取 [組建]  >  [組建方案]。 您也可以編譯並執行應用程式的偵錯組建，方法是選取 [偵錯]  >  [開始偵錯]。

1. 發行您的應用程式。

   在您偵錯並測試程式之後，請針對每個目標平台建立要隨應用程式一起部署的檔案。

   若要從 Visual Studio 發行您的應用程式，請執行下列作業：

      1. 在工具列上將方案組態從 [偵錯] 變更為 [發行]，以組建應用程式的發行 (而不是偵錯) 版本。

      1. 以滑鼠右鍵按一下方案總管中的專案 (而非方案)，然後選取 [發行]。 

      1. 在 [發行] 索引標籤中，選取 [發行]。 Visual Studio 會將構成應用程式的檔案寫入至本機檔案系統。

      1. [發行] 索引標籤現在會顯示單一設定檔 **FolderProfile**。 設定檔的組態設定顯示在索引標籤的 [摘要] 區段中。[目標執行階段] 識別已發行的執行階段，而 [目標位置] 則識別自封式部署的檔案寫入位置。

      1. Visual Studio 預設會將所有發行的檔案寫入到單一目錄。 為了方便起見，最好是建立每個目標執行階段的個別設定檔，並將已發行的檔案放在特定平台目錄中。 這牽涉到建立每個目標平台的個別發行設定檔。 因此，現在請執行下列作業來重建每個平台的應用程式：

         1. 選取 [建立新設定檔] 中的 [發行] 對話方塊。

         1. 在 [挑選發行目標] 對話方塊中，將 [選擇資料夾] 位置變更為 *bin\Release\PublishOutput\win10 x64*。 選取 [確定]。

         1. 選取設定檔清單中的新設定檔 (**FolderProfile1**)，並確定 [目標執行階段] 是 `win10-x64`。 如果不是，請選取 [設定]。 在 [設定檔設定] 對話方塊中，將 [目標執行階段] 變更為 `win10-x64`，然後選取 [儲存]。 否則，請選取 [取消]。

         1. 選取 [發行] 來發行適用於 64 位元 Windows 10 平台的應用程式。

         1. 請再次遵循上述步驟，以建立適用於 `osx.10.11-x64` 平台的設定檔。 [目標位置] 是 *bin\Release\PublishOutput\osx.10.11-x64*，而 [目標執行階段] 是 `osx.10.11-x64`。 Visual Studio 指派給此設定檔的名稱是 **FolderProfile2**。

      請注意，每個目標位置都包含啟動應用程式所需的一組完整檔案 (應用程式檔案和所有的 .NET Core 檔案)。

隨著應用程式檔案一起，發佈程序會發出程式資料庫 (.pdb) 檔案，其中包含應用程式的偵錯資訊。 該檔案主要是用於例外狀況偵錯。 您可以選擇不與您的應用程式檔案一起封裝它。 不過，如果您要對應用程式的發行組建進行偵錯，則應該將其儲存。

請使用任何您想要的方式，部署已發行的檔案。 例如，您可以使用簡單的 `copy` 命令將它們封裝在 ZIP 檔案中，或與您選擇的任何安裝套件一起部署。

下面是此專案的完整 *csproj* 檔案。

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

## <a name="self-contained-deployment-with-third-party-dependencies"></a>有協力廠商相依性的自封式部署

部署具有一或多個協力廠商相依性的自封式部署，涉及新增相依性。 在組建您的應用程式之前，需要執行下列其他步驟：

1. 使用 [NuGet 套件管理員]，將 NuGet 套件的參考新增至您的專案；如果您的系統上還沒有該套件，請安裝它。 若要開啟套件管理員，請選取 [工具]  >  [NuGet 套件管理員]  >  [管理方案的 NuGet 套件]。

1. 確認 `Newtonsoft.Json` 已安裝在您的系統上，如果尚未安裝，請安裝它。 [已安裝] 索引標籤會列出您系統上已安裝的 NuGet 套件。 如果 `Newtonsoft.Json` 未列於該處，請選取 [瀏覽] 索引標籤，然後在 [搜尋] 方塊中輸入 "Newtonsoft.Json"。 選取 `Newtonsoft.Json`，並先在右窗格中選取您的專案，然後選取 [安裝]。

1. 如果 `Newtonsoft.Json` 已安裝在您的系統上，請在 [管理方案的封裝] 索引標籤的右窗格中選取您的專案，以將它新增至您的專案。

下面是此專案的完整 *csproj* 檔案：

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64</RuntimeIdentifiers>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.2" />
  </ItemGroup>
</Project>
```

當您部署應用程式時，應用程式中任何協力廠商相依性也包含在應用程式檔案中。 應用程式執行所在的系統上不需要協力廠商程式庫。

請注意，您只能將具有協力廠商程式庫的自封式部署，部署到該程式庫支援的平台上。 這類似於在與 Framework 相依的部署中擁有仰賴原生相依性的協力廠商相依性；在其中，原生相依性不會存在於目標平台上，除非先前已在該處安裝這些相依性。

# <a name="see-also"></a>另請參閱
[.NET Core 應用程式部署](index.md)   
[.NET Core 執行階段識別項 (RID) 目錄](../rid-catalog.md)   
