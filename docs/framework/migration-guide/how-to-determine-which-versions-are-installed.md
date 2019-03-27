---
title: 作法：判斷安裝的 .NET Framework 版本
ms.date: 03/18/2019
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
ms.openlocfilehash: 8b7c7704c4f417ef16d3a79fa6d955265e42cf14
ms.sourcegitcommit: e994e47d3582bf09ae487ecbd53c0dac30aebaf7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2019
ms.locfileid: "58262444"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>作法：判斷安裝的 .NET Framework 版本

使用者可以在電腦上[安裝](https://docs.microsoft.com/dotnet/framework/install)及執行多個版本的 .NET Framework。 當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。 

.NET Framework 包含兩個主要元件，各有各的版本控制：  
  
- 組件集合，這是為應用程式提供功能的類型與資源集合。 .NET Framework 和組件會共用相同的版本號碼。  
  
- 通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。 CLR 是透過自己的版本號碼加以識別 (請參閱[版本和相依性](~/docs/framework/migration-guide/versions-and-dependencies.md))。  

> [!NOTE]
> 每一個新的 .NET Framework 版本都會保留舊版的功能並增加新的功能。 您可同時在一部電腦上載入多個版本的 .NET Framework，這表示您可以安裝 .NET Framework，卻不必解除安裝舊版。 一般而言，您不應該解除安裝舊版的 .NET Framework，因為您使用的應用程式可能依賴某個特定版本，而若移除該版本則應用程式可能會中斷。
>
> .NET Framework 版本和 CLR 版本之間有差異： 
> - .NET Framework 版本是以構成 .NET Framework Class Library 的組件集為基礎。 例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。 
>- CLR 版本是以 .NET Framework 應用程式執行所在的執行階段為基礎。 單一的 CLR 版本通常會支援多個 .NET Framework 版本。 例如，CLR 4.0.30319.*xxxxx* 版支援 .NET Framework 4 到 4.5.2 版，而 CLR 4.0.30319.42000 版支援從 .NET Framework 4.6 起的 .NET Framework 版本。 
>
> 如需版本的詳細資訊，請參閱 [.NET Framework 版本和相依性](versions-and-dependencies.md)。


您可以存取登錄來取得電腦上安裝的 .NET Framework 版本清單。 您可以使用登錄編輯程式來檢視登錄，或使用程式碼來查詢登錄：
 
- 尋找新版的 .NET Framework (4.5 和更新版本)： 
     - [使用登錄編輯程式尋找 .NET Framework 版本](#net_b)  
     - [使用程式碼查詢登錄以取得 .NET Framework 版本](#net_d)  
     - [使用 PowerShell 查詢登錄以取得 .NET Framework 版本](#ps_a)
 - 尋找舊版的 .NET Framework (1&#8211;4)：
     - [使用登錄編輯程式尋找 .NET Framework 版本](#net_a)
     - [使用程式碼查詢登錄以取得 .NET Framework 版本](#net_c)   

使用工具或程式碼取得安裝在電腦上的 CLR 版本清單：  
  
 - [使用 Clrver 工具](#clr_a)  
 - [使用程式碼查詢 Environment 類別](#clr_b)  

如需偵測每一版 .NET Framework 已安裝更新的資訊，請參閱[如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a>尋找新版的 .NET Framework (4.5 和更新版本)

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>在登錄中尋找 .NET Framework 4.5 和更新版本

1. 從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。

     您必須具有系統管理認證才能執行 regedit。

2. 在 [登錄編輯程式] 中，開啟下列子機碼：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**。 如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。

    > [!NOTE]
    > 登錄中的 **NET Framework Setup** 資料夾不是以英文句號開頭。

3. 檢查是否有名為 **Release** 的 DWORD 項目。 若有，則表示已安裝 .NET Framework 4.5 或更新版本。 其值為對應至 .NET Framework 特定版本的版本機碼。 例如，下圖中 **Release** 項目的值是 *378389*，也就是 .NET Framework 4.5 的版本機碼。 

     ![.NET Framework 4.5 的登錄項目](media/clr-installdir.png ".NET Framework 4.5 的登錄項目")

下表列出每個 .NET Framework 版本 **Release** 項目的最小值。 您可以依照下列方式使用這些值：

- 若要判斷最低的 .NET Framework 版本是否存在，請測試登錄中所找到 **Release** DWORD 值是否「大於或等於」資料表中所列的值。 例如，如果您的應用程式需要 .NET Framework 4.7 或更新版本，您要測試是否有 *460798* 的最低版本機碼值。

- 若要測試多個版本，請從最新的 .NET Framework 版本開始，然後依序回推每個舊版進行測試。

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

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


<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a>使用程式碼尋找 .NET Framework 4.5 和更新版本

1. 使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼。

    **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼中存在 **Release** DWORD 項目表示 .NET Framework 4.5 或更新版本已安裝在電腦上。 

2. 檢查 **Release** 項目的值，判斷已安裝的版本。 若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。

下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

此範例遵循版本檢查的建議做法：

- 它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。

- 它會從最新版本依序檢查到最舊版本。

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>使用 PowerShell 檢查 .NET Framework 最低版本需求 (4.5 及更新版本)

- 使用 PowerShell 命令檢查 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full** 子機碼的 **Release** 項目值。

下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。 如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
```

若要檢查不同的所需 .NET Framework 最低版本，請以 [.NET Framework 版本表](#version_table)的 **Release** 值取代這些範例中的 *394802*。

## <a name="find-older-net-framework-versions-182114"></a>尋找舊版的 .NET Framework (1&#8211;4)

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a>在登錄中尋找 .NET Framework 1&#8211;4 版 
  
1. 從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。
  
    您必須具有系統管理認證才能執行 regedit。  

2. 在 [登錄編輯程式] 中，開啟下列子機碼：**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**：  

    - 針對 .NET Framework 1.1 到 3.5 版，每個安裝的版本都會列為 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** 子機碼下的子機碼。 例如，**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**。 版本號碼儲存為版本子機碼 **Version** 項目中的值。 
     
    - 以 .NET Framework 4 為例，**Version** 項目位在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** 及/或 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full** 子機碼下。

    > [!NOTE]
    > 登錄中的 **NET Framework Setup** 資料夾不是以英文句號開頭。

    下圖顯示 .NET Framework 3.5 的子機碼及其 **Version** 項目。

    ![.NET Framework 3.5 的登錄項目。](media/net-4-and-earlier.png ".NET framework 3.5 和舊版")

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a>使用程式碼尋找 .NET Framework 1&#8211;4 版

- 使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** 子機碼。

下列範例會尋找已安裝的 .NET Framework 1&#8211;4 版：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a>尋找 CLR 版本
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a>使用 Clrver.exe 尋找目前的 CLR 版本

使用 [CLR 版本工具 (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) 以判斷電腦上安裝了哪些 CLR 版本：

- 從 [Visual Studio 的開發人員命令提示字元](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs)輸入 `clrver`。

    範例輸出：

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a>使用環境類別尋找目前的 CLR 版本

> [!IMPORTANT]
> 針對 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性偵測 CLR 的版本。 請依[使用程式碼尋找 .NET Framework 4.5 和更新版本](#net_d)中所述，改查詢登錄。

1. 查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。 

    傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。 它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。

    針對 .NET Framework 4、4.5、4.5.1 和 4.5.2 版，所傳回 <xref:System.Version> 物件的字串表示格式為 4.0.30319.*xxxxx*。 針對 .NET Framework 4.6 和更新版本，其格式為 4.0.30319.42000。    

2. 取得 `Version` 物件之後，如下所示來加以查詢：

   - 針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。

   - 針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。

   - 針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。 這個方法會傳回單一值，其反映執行程式碼的執行階段版本。 它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。



下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>另請參閱

- [如何：判斷安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)
- [安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)
- [.NET Framework 版本和相依性](versions-and-dependencies.md)
