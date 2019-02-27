---
title: HOW TO：判斷安裝的 .NET Framework 版本
ms.date: 02/20/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584170"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>作法：判斷安裝的 .NET Framework 版本

使用者可以在電腦上安裝及執行多個版本的 .NET Framework。 當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。 請注意，.NET Framework 包含兩個主要元件，這兩個元件的版本控制會分開處理：  
  
- 組件集合，這是為應用程式提供功能的類型與資源集合。 .NET Framework 和組件會共用相同的版本號碼。  
  
- 通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。 CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。  
  
若要取得電腦上安裝之 .NET Framework 版本的正確清單，您可以檢視登錄或查詢程式碼中的登錄：  
  
 [在登錄中尋找 .NET Framework 1-4 版](#net_a)  
 [在登錄中尋找 .NET Framework 4.5 和更新版本](#net_b)  
 [使用程式碼查詢登錄 (1-4 版)](#net_c)  
 [使用程式碼查詢登錄 (4.5 版及更新版本)](#net_d)  
 [使用 PowerShell 查詢登錄 (4.5 版及更新版本)](#ps_a)  

 若要尋找 CLR 版本，您可以使用工具或程式碼：  
  
 [使用 Clrver 工具](#clr_a)  
 [使用程式碼查詢 System.Environment 類別](#clr_b)  

> [!NOTE]
> .NET Framework 版本和通用語言執行平台 (CLR) 版本之間有下列差異。 .NET Framework 的版本建立是以構成 .NET Framework Class Library 的組件集為基礎。 例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。 CLR 的版本建立是以 .NET Framework 應用程式執行的執行階段為依據，且單一 CLR 版本通常可支援多個 .NET Framework 版本。 CLR 4.30319.*xxxxx* 版支援 .NET Framework 4 到 4.5.2 版；CLR 4.30319.42000 版支援從 .NET Framework 4.6 起的 .NET Framework 版本。 如需詳細資訊，請參閱 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性 (Property)。

 如需偵測每一版 .NET Framework 已安裝更新的資訊，請參閱[如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)。 如需安裝 .NET Framework 的資訊，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)。  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>在登錄中尋找 .NET Framework 1-4 版 
  
1.  在 [開始] 功能表中選擇 [執行]。  
  
2.  在 [開啟] 方塊中輸入 **regedit.exe**。  
  
     您必須具有系統管理認證才能執行 regedit.exe。  
  
3.  在 [登錄編輯程式] 中，開啟下列子機碼：  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     若為 .NET Framework 1.1 到 3.5 版，已安裝版本會列為 `NDP` 子機碼下方的子機碼。 版本號碼儲存在版本子機碼的 **Version** 項目中。 
     
     若為 .NET Framework 4，則 **Version** 項目位於 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` 子機碼下方、`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` 子機碼下方，或這兩個子機碼下方。

    > [!NOTE]
    > 登錄中的 [NET Framework Setup] 資料夾不是以英文句號開頭。

    下圖顯示 .NET Framework 3.5 的子機碼與其 **Version** 項目。

     ![.NET Framework 3.5 的登錄項目。](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 和更早版本")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>在登錄中尋找 .NET Framework 4.5 和更新版本

1. 在 [開始] 功能表中選擇 [執行]。

2. 在 [開啟] 方塊中輸入 **regedit.exe**。

     您必須具有系統管理認證才能執行 regedit.exe。

3. 在 [登錄編輯程式] 中，開啟下列子機碼：

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     請注意，路徑 `Full` 子機碼包含子機碼 `Net Framework` 而非`.NET Framework`。

    > [!NOTE]
    > 如果 `Full` 子機碼不存在，則您未安裝 .NET Framework 4.5 或更新版本。

     檢查名為 `Release` 的 DWORD 值。 如果 `Release` DWORD 存在，即表示該電腦上已安裝 .NET Framework 4.5 或更新版本。 其值為對應至 .NET Framework 特定版本的版本機碼。 例如，下圖中 `Release` DWORD 的值是 378389，也就是 .NET Framework 4.5 的版本機碼。 

     ![.NET Framework 4.5 的登錄項目。](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

下表列出每個 .NET Framework 版本的 `Release` DWORD 最小值。 您可以依照下列方式使用這些值：

- 若要判斷最低的 .NET Framework 版本是否存在，請測試登錄中找到的 `Release` DWORD 值是否「大於或等於」資料表中所列的值。 例如，如果您的應用程式需要 .NET Framework 4.7 或更新版本，您將進行測試以尋找 460798 的最低版本機碼值。

- 若要測試多個版本，請從最新的 .NET Framework 版本開始，然後依序回推每個舊版進行測試。

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|.NET Framework 版本|Release DWORD 的值|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET Framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

如需特定 Windows 作業系統版本的 .NET Framework 版本機碼完整資料表，請參閱 [.NET Framework 版本機碼和 Windows 作業系統版本](release-keys-and-os-versions.md)。

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>使用程式碼尋找 .NET Framework 1-4 版

- 使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別來存取 Windows 登錄中 `HKEY_LOCAL_MACHINE` 分支下方的 `Software\Microsoft\NET Framework Setup\NDP\` 子機碼。

     下列程式碼將示範此查詢的範例。

    > [!NOTE]
    > 這個程式碼不會示範如何偵測 .NET Framework 4.5 或更新版本。 檢查 `Release` DWORD 即可偵測這些版本，如上一節所述。 如需可偵測 .NET Framework 4.5 或更新版本的程式碼，請參閱本文中的下一節。

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>使用程式碼尋找 .NET Framework 4.5 和更新版本

1. 如果 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 機碼中存在 `Release` DWORD，即表示電腦上已安裝 .NET Framework 4.5 或更新版本。 關鍵字的值表示已安裝的版本。 若要檢查此機碼，請使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法來存取 Windows 登錄中的子機碼。

2. 檢查 `Release` 關鍵字的值，判斷已安裝的版本。 若要向前相容，您可以檢查是否有值大於或等於[在登錄中尋找 .NET Framework 4.5 和更新版本](#net_b)一節中資料表所列的值。

下列範例會檢查登錄中的 `Release` 值來判斷是否已安裝 .NET Framework 4.5 或更新版本。

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

此範例遵循版本檢查的建議做法：

- 它會檢查 `Release` 項目的值「大於或等於」已知版本機碼的值。

- 它會從最新版本依序檢查到最舊版本。

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>使用 PowerShell 檢查 .NET Framework 最低版本需求 (4.5 及更新版本)

下列範例會檢查 `Release` 關鍵字的值，判斷是否已安裝 .NET Framework 4.6.2 或更新版本 (如果是，傳回 `True`；否則傳回 `False`)。

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>使用 Clrver.exe 尋找目前的 CLR 版本

使用 CLR 版本工具 (Clrver.exe) 判斷電腦上安裝了哪些通用語言執行平台 (CLR) 版本。

從 Visual Studio 開發人員命令提示字元輸入 `clrver`。 這個命令產生的輸出類似下面所述：

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

如需使用這項工具的詳細資訊，請參閱 [Clrver.exe (CLR 版本工具)](~/docs/framework/tools/clrver-exe-clr-version-tool.md)。

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>使用環境類別尋找目前的 CLR 版本

透過擷取 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性值，您可以擷取 <xref:System.Version> 來識別目前執行程式碼的執行階段版本。 這個屬性會傳回單一值，以反映出目前執行程式碼的執行階段版本，但是不會傳回電腦上可能已安裝的組件版本或其他執行階段版本。您可以使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性取得主要版本識別碼 (例如，"4" 代表 4.0 版)、使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性取得次要版本識別碼 (例如，"0" 代表 4.0 版)，或使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法取得整個版本字串 (例如 "4.0.30319.18010"，如下列程式碼所示)。 

針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，<xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性會傳回 <xref:System.Version> 物件，其字串表示的格式為 `4.0.30319.xxxxx`。 針對 .NET Framework 4.6 和更新版本，其格式為 `4.0.30319.42000`。

> [!IMPORTANT]
> 針對 .NET Framework 4.5 和更新版本，不建議使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測執行階段的版本。 相反地，建議您查詢登錄，如本文稍早的[藉由查詢程式碼中的登錄尋找 .NET Framework 版本 (.NET Framework 4.5 及更新版本)](#net_d) 一節中所述。

下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取執行階段版本資訊：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>另請參閱

- [如何：判斷安裝的 .NET Framework 更新](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)
- [版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md)
