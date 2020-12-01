---
title: 判斷安裝的 .NET Framework 版本
description: 藉由查詢 Windows 登錄，使用程式碼、regedit.exe 或 PowerShell 來偵測電腦上所安裝的 .NET Framework 版本。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: b4c5b6911a4be4f9ac156b600646c649549f88f8
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96438133"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>如何：判斷安裝的 .NET Framework 版本

使用者可以在其電腦上 [安裝](../install/index.md) 及執行多個版本的 .NET Framework。 當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。 登錄包含電腦上所安裝 .NET Framework 版本的清單。

.NET Framework 是由兩個主要元件所組成，這些元件分別設定版本：

- 組件集合，這是為應用程式提供功能的類型與資源集合。 .NET Framework，且元件共用相同的版本號碼。 例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。

- 通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。 單一的 CLR 版本通常會支援多個 .NET Framework 版本。 例如，CLR 版本4.0.30319。*xxxxx 小於* 42000 的 *xxxxx* 支援 .NET Framework 版本4到4.5.2。 大於或等於4.0.30319.42000 版的 CLR 版本支援從 .NET Framework 4.6 開始的 .NET Framework 版本。

您可以使用由社區維護的工具，來協助偵測已安裝哪些 .NET Framework 版本：

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  .NET Framework 2.0 命令列工具。

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  PowerShell 2.0 模組。

如需有關針對每個 .NET Framework 版本偵測已安裝之更新的詳細資訊，請參閱 [如何：判斷已安裝哪些 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。

## <a name="detect-net-framework-45-and-later-versions"></a>偵測 .NET Framework 4.5 和更新版本

電腦上安裝的 .NET Framework (4.5 和更新版本) 會列在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 的登錄中。 如果遺失 **完整** 子機碼，則不會安裝 .NET Framework 4.5 或更新版本。

> [!NOTE]
> 登錄路徑中的 **NET Framework Setup** 子機碼開頭 *不* 是句點。

登錄中的 **版本 REG_DWORD 值** 代表安裝的 .NET Framework 版本。

<a name="version_table"></a>

| .NET Framework 版本 | **發行** 的值 |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | 所有 Windows 作業系統：378389 |
| .NET Framework 4.5.1   | 在 Windows 8.1 和 Windows Server 2012 R2：378675<br />在所有其他 Windows 作業系統上：378758 |
| .NET Framework 4.5.2   | 所有 Windows 作業系統：379893 |
| .NET Framework 4.6     | 在 Windows 10: 393295 上<br />在所有其他 Windows 作業系統上：393297 |
| .NET Framework 4.6.1   | Windows 10 11 月更新系統：394254<br />在所有其他 Windows 作業系統上 (包括 Windows 10) ：394271 |
| .NET Framework 4.6.2   | Windows 10 年度更新版及 Windows Server 2016：394802<br />在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：394806 |
| .NET Framework 4.7     | Windows 10 Creators Update：460798<br />在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：460805 |
| .NET Framework 4.7.1   | 在 Windows 10 Fall Creators Update 和 Windows Server 上，版本1709：461308<br/>在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：461310 |
| .NET Framework 4.7.2   | 在 Windows 10 2018 年4月更新和 Windows Server 上，版本1803：461808<br/>在 Windows 10 2018 年4月更新和 Windows Server 以外的所有 Windows 作業系統上，版本1803：461814 |
| .NET Framework 4.8     | 在 Windows 10 2019 年5月更新和 Windows 10 2019 年11月更新：528040<br/>在 Windows 10 5 月2020更新和 Windows 10 2020 年10月更新：528372<br/>在所有其他 Windows 作業系統上 (包括其他 Windows 10 作業系統) ：528049 |

### <a name="minimum-version"></a>最小版本

若要判斷 .NET Framework 的 *最小* 版本是否存在，請檢查是否有大於或等於下表所列對應值的 **發行** REG_DWORD 值。 例如，如果您的應用程式在 .NET Framework 4.8 或更新版本下執行，請測試 *大於或等於* 528040 的 **發行** REG_DWORD 值。

| .NET Framework 版本 | 最小值 |
| ---------------------- | ------------- |
| .NET Framework 4.5     | 378389 |
| .NET Framework 4.5.1   | 378675 |
| .NET Framework 4.5.2   | 379893 |
| .NET Framework 4.6     | 393295 |
| .NET Framework 4.6.1   | 394254 |
| .NET Framework 4.6.2   | 394802 |
| .NET Framework 4.7     | 460798 |
| .NET Framework 4.7.1   | 461308 |
| .NET Framework 4.7.2   | 461808 |
| .NET Framework 4.8     | 528040 |

### <a name="use-registry-editor"></a>使用登錄編輯程式

01. 從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。

    (您必須擁有系統管理認證才能執行 regedit。 ) 

01. 在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**。 如果 **完整** 的子機碼不存在，您就不會安裝 .NET Framework 4.5 或更新版本。

01. 檢查名為 **Release** 的 REG_DWORD 專案。 如果存在，表示您已安裝 .NET Framework 4.5 或更新版本。 其值會對應至特定版本的 .NET Framework。 例如，在下圖中， **發行** 專案的值是528040，也就是 .NET Framework 4.8 的發行金鑰。

   ![.NET Framework 4.5 的登錄專案](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a>使用 PowerShell 檢查最低版本

使用 PowerShell 命令來檢查 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ V4 \\ Full** 子機碼的 **發行** 專案值。

下列範例會檢查 **發行** 專案的值，以判斷是否已安裝 .NET Framework 4.6.2 或更新版本。 如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。

```powershell
(Get-ItemProperty "HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>使用程式碼查詢登錄

01. 使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法來存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full** 子機碼。

    > [!IMPORTANT]
    > 如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。 例如，.NET Framework 4.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**。

01. 檢查 **發行** REG_DWORD 值，以判斷已安裝的版本。 若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。

下列範例會檢查登錄中 **發行** 專案的值，以尋找已安裝 .NET Framework 4.5-4.8 的版本：

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

此範例會顯示如下所示的輸出：

```output
.NET Framework Version: 4.6.1
```

此範例遵循版本檢查的建議做法：

- 它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。
- 它會從最新版本依序檢查到最舊版本。

## <a name="detect-net-framework-10-through-40"></a>偵測 .NET Framework 1.0 至4。0

從1.1 到 4.0 .NET Framework 的每個版本都會在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ .net Framework 安裝 \\ NDP** 中列為子機碼。 下表列出每個 .NET Framework 版本的路徑。 大部分的版本都有 **安裝** REG_DWORD 值，表示已 `1` 安裝此版本。 在這些子機碼中，也有包含版本字串的 REG_SZ 值 **版本** 。

> [!NOTE]
> 登錄路徑中的 **NET Framework Setup** 子機碼開頭 *不* 是句點。

| Framework 版本  | 登錄子機碼 | 值 |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM \\ Software \\ Microsoft \\ 。.Netframework \\ 原則 \\ 1.0 版 \\ 3705**     | **安裝** REG_SZ equals `1` |
| 1.1                | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 1.1.4322**   | **安裝** REG_DWORD equals `1` |
| 2.0                | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 2.0.50727**  | **安裝** REG_DWORD equals `1` |
| 3.0                | **HKLM \\ Software \\ Microsoft \\ NET Framework setup \\ NDP \\ v3.0 \\ 設定** | **InstallSuccess** REG_DWORD equals `1` |
| 3.5                | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3。5**        | **安裝** REG_DWORD equals `1` |
| 4.0 用戶端設定檔 | **HKLM \\ Software \\ Microsoft \\ NET Framework 設定 \\ NDP \\ v4 \\ 用戶端**  | **安裝** REG_DWORD equals `1` |
| 4.0 完整設定檔   | **HKLM \\ Software \\ Microsoft \\ NET Framework Setup \\ NDP \\ v4 \\ Full**    | **安裝** REG_DWORD equals `1` |

> [!IMPORTANT]
> 如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。 例如，.NET Framework 3.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**。

請注意，.NET Framework 1.0 子機碼的登錄路徑與其他子機碼不同。

### <a name="use-registry-editor-older-framework-versions"></a>使用 (舊版 framework 的登錄編輯程式) 

01. 從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。

    您必須具有系統管理認證才能執行 regedit。

01. 開啟符合您要檢查之版本的子機碼。 使用「偵測 [.NET Framework 1.0 至 4.0](#detect-net-framework-10-through-40) 」一節中的表格。

    下圖顯示 .NET Framework 3.5 的子機碼及其 **版本** 值。

    ![.NET Framework 3.5 的登錄專案。](./media/net-4-and-earlier.png ".NET Framework 3.5 及更早版本")

### <a name="query-the-registry-using-code-older-framework-versions"></a>使用 (舊版 framework 的程式碼查詢登錄) 

使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別存取 Windows 登錄中的 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Microsoft \\ .net Framework 安裝 \\ NDP** 子機碼。

> [!IMPORTANT]
> 如果您正在執行的應用程式是32位並在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 您可以在 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\** 子機碼中找到64位登錄。 例如，.NET Framework 3.5 的登錄子機碼是 **HKEY_LOCAL_MACHINE \\ SOFTWARE \\ Wow6432Node \\ Microsoft \\ NET Framework Setup \\ NDP \\ v 3.5**。

下列範例會尋找已安裝的 .NET Framework 1-4 版本：

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

此範例會顯示如下所示的輸出：

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a>尋找 CLR 版本

隨 .NET Framework 安裝的 .NET Framework CLR 會分開建立版本。 有兩種方式可以偵測 .NET Framework CLR 的版本：

- **Clrver.exe 工具**

  使用 [Clr 版本工具 ( # A0) ](../tools/clrver-exe-clr-version-tool.md) 來判斷電腦上安裝的 clr 版本。 開啟 [Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md) ，然後輸入 `clrver` 。

  範例輸出：

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **`Environment`類別**

  > [!IMPORTANT]
  > 針對 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測 CLR 版本。 請改為查詢登錄，如偵測 [.NET Framework 4.5 和更新版本](#detect-net-framework-45-and-later-versions)中所述。

  1. 查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。

     傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。 它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。

     針對 .NET Framework 4、4.5、4.5.1 和4.5.2 版，所傳回物件的字串表示 <xref:System.Version> 格式為4.0.30319。*xxxxx*，其中 *xxxxx* 小於42000。 針對 .NET Framework 4.6 和更新版本，其格式為4.0.30319.42000 版。

  1. 取得 **版本** 物件之後，請依照下列方式進行查詢：

     - 針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。

     - 針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。

     - 針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。 這個方法會傳回單一值，其反映執行程式碼的執行階段版本。 它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。

  下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  此範例會顯示如下所示的輸出：

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a>另請參閱

- [如何：判斷安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)
- [安裝適用于開發人員的 .NET Framework](../install/guide-for-developers.md)
- [.NET Framework 版本和相依性](versions-and-dependencies.md)
