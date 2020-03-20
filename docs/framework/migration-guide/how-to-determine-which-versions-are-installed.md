---
title: 判斷安裝的 .NET Framework 版本
description: 使用代碼、regedit.exe 或 PowerShell 通過查詢 Windows 註冊表來檢測電腦上安裝的 .NET Framework 的哪些版本。
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: 8469f977c6ed9691c81a2a8354935557b5c27171
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "77093823"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>如何：判斷安裝的 .NET Framework 版本

使用者可以在其電腦上[安裝](../install/index.md)和運行多個版本的 .NET 框架。 當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。 註冊表包含電腦上安裝的 .NET 框架版本的清單。

.NET Framework 包含兩個主要元件，各有各的版本控制：

- 組件集合，這是為應用程式提供功能的類型與資源集合。 .NET Framework 和組件會共用相同的版本號碼。 例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。

- 通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。 單一的 CLR 版本通常會支援多個 .NET Framework 版本。 例如，CLR 版本 4.0.30319。*xxxxx* *xxxxxxxxxx*的 xxxxx 小於 42000，支援 .NET 框架版本 4 到 4.5.2。 CLR 版本大於或等於 4.0.30319.42000 支援 .NET 框架版本，以 .NET 框架 4.6 開頭。

社區維護的工具可説明檢測安裝了哪些 .NET Framework 版本：

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  .NET 2.0 命令列工具。

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  PowerShell 2.0 模組。

有關檢測每個版本的 .NET Framework 的已安裝更新的資訊，請參閱[如何：確定安裝了哪些 .NET 框架更新](how-to-determine-which-net-framework-updates-are-installed.md)。

## <a name="detect-net-framework-45-and-later-versions"></a>檢測 .NET 框架 4.5 和更高版本

安裝在電腦上的 .NET 框架（4.5 及更高版本）的版本列在**註冊表中，HKEY_LOCAL_MACHINE\\\\軟體 Microsoft\\NET\\框架\\設置\\NDP v4 完整**。 如果缺少**完整**子鍵，則未安裝 .NET 框架 4.5 或以上。

> [!NOTE]
> 註冊表路徑中的**NET 框架設置**子鍵*不*以句點開頭。

**註冊表中的"版本**REG_DWORD"值表示已安裝的 .NET 框架的版本。

<a name="version_table"></a>

| .NET Framework 版本 | **釋放**價值 |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | 所有 Windows 作業系統： 378389 |
| .NET Framework 4.5.1   | 在 Windows 8.1 和 Windows 伺服器 2012 R2： 378675<br />在所有其他 Windows 作業系統上： 378758 |
| .NET Framework 4.5.2   | 所有 Windows 作業系統： 379893 |
| .NET Framework 4.6     | 在 Windows 10 上： 393295<br />在所有其他 Windows 作業系統上： 393297 |
| .NET Framework 4.6.1   | Windows 10 11 月更新系統：394254<br />在所有其他 Windows 作業系統（包括 Windows 10）：394271 |
| .NET Framework 4.6.2   | Windows 10 年度更新版及 Windows Server 2016：394802<br />在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：394806 |
| .NET Framework 4.7     | Windows 10 Creators Update：460798<br />在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：460805 |
| .NET Framework 4.7.1   | 在 Windows 10 秋季建立者更新和 Windows 伺服器上，版本 1709： 461308<br/>在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：461310 |
| .NET Framework 4.7.2   | 在 Windows 10 四月 2018 更新和 Windows 伺服器， 版本 1803： 461808<br/>在 Windows 10 2018 更新和 Windows 伺服器以外的所有 Windows 作業系統上，版本 1803： 461814 |
| .NET Framework 4.8     | 在 Windows 10 五月 2019 更新和 Windows 10 十一月 2019 更新： 528040<br/>在 Windows 10 和 Windows 伺服器上，版本 1909： 528209<br/>在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）：528049 |

### <a name="minimum-version"></a>最小版本

要確定是否存在 .NET 框架*的最小*版本，請使用上表中該版本的最小**版本**REG_DWORD值。

例如，如果應用程式在 .NET Framework 4.8 或更高版本下運行，則測試**版本**REG_DWORD*值大於或等於*528040。

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

01. 從 [開始]**** 功能表上，選擇 [執行]****，輸入 *regedit*，然後選取 [確定]****。

    您必須具有系統管理認證才能執行 regedit。

01. 在登錄編輯程式中，打開以下子鍵 **：HKEY_LOCAL_MACHINE\\軟體微軟\\\\NET 框架\\設置\\NDP\\v4 完整**。 如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。

01. 檢查名為 **"版本**"的REG_DWORD條目。 如果存在，則已安裝 .NET 框架 4.5 或更高版本。 其值對應于 .NET 框架的特定版本。 例如，在下圖中，**發佈**條目的值為 528040，這是 .NET Framework 4.8 的發佈鍵。

    ![.NET 框架 4.5 的登錄機碼](./media/clr-installdir.png ".NET 框架 4.5 的登錄機碼")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>使用 PowerShell 檢查最小版本

使用 PowerShell 命令檢查**\\HKEY_LOCAL_MACHINE軟體 Microsoft\\\\NET 框架設置\\NDP\\v4\\完整**子鍵的**發佈**條目的值。

下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。 如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>使用代碼查詢註冊表

01. 使用<xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType>和<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>方法訪問**windows\\\\註冊表\\中HKEY_LOCAL_MACHINE軟體\\\\Microsoft\\NET 框架設置 NDP v4 完全**子鍵。

    > [!IMPORTANT]
    > 如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。 64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。 例如，.NET 框架 4.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架\\設置 NDP v4 完整**。

01. 檢查 **"發佈**REG_DWORD"值以確定已安裝的版本。 若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。

下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

此範例遵循版本檢查的建議做法：

- 它會檢查 **Release** 項目值是否「大於或等於」** 已知版本機碼的值。
- 它會從最新版本依序檢查到最舊版本。

## <a name="detect-net-framework-10-through-40"></a>檢測 .NET 框架 1.0 到 4.0

每個版本的 .NET 框架從 1.1 到 4.0 被列為子**鍵\\在\\\\HKEY_LOCAL_MACHINE軟體微軟\\NET 框架設置 NDP**. 下表列出了每個 .NET 框架版本的路徑。 對於大多數版本，有一個**安裝**REG_DWORD值`1`，以指示已安裝此版本。 在這些子鍵中，還有一個包含版本字串**的版本**REG_SZ值。

> [!NOTE]
> 註冊表路徑中的**NET 框架設置**子鍵*不*以句點開頭。

| 框架版本  | 註冊表子鍵 | 值 |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\軟體\\微軟\\。NETFramework\\\\策略 v1.0\\3705**     | **安裝**REG_SZ等於`1` |
| 1.1                | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v1.1.4322**   | **安裝**REG_DWORD等於`1` |
| 2.0                | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v2.0.50727**  | **安裝**REG_DWORD等於`1` |
| 3.0                | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v3.0\\設置** | **安裝成功**REG_DWORD等於`1` |
| 3.5                | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v3.5**        | **安裝**REG_DWORD等於`1` |
| 4.0 用戶端設定檔 | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v4\\用戶端**  | **安裝**REG_DWORD等於`1` |
| 4.0 完整設定檔   | **HKLM\\軟體\\微軟\\NET框架設置\\NDP\\v4\\完整**    | **安裝**REG_DWORD等於`1` |

> [!IMPORTANT]
> 如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。 64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。 例如，.NET 框架 3.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架設置 NDP v3.5**。

請注意，.NET 框架 1.0 子鍵的註冊表路徑與其他子項不同。

### <a name="use-registry-editor-older-framework-versions"></a>使用登錄編輯程式（較舊的框架版本）

01. 從 [開始]**** 功能表上，選擇 [執行]****，輸入 *regedit*，然後選取 [確定]****。

    您必須具有系統管理認證才能執行 regedit。

01. 打開與要檢查的版本匹配的子鍵。 使用[檢測 .NET 框架 1.0 到 4.0](#detect-net-framework-10-through-40)部分中的表。

    下圖顯示了 .NET 框架 3.5 的子鍵及其**版本**值。

    ![.NET 框架 3.5 的登錄機碼。](./media/net-4-and-earlier.png ".NET 框架 3.5 及早期版本")

### <a name="query-the-registry-using-code-older-framework-versions"></a>使用代碼查詢註冊表（較舊的框架版本）

使用<xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>該類訪問 Windows 註冊表中**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET 框架設置\\NDP**子鍵。

> [!IMPORTANT]
> 如果您正在運行的應用為 32 位並在 64 位 Windows 中運行，則註冊表路徑將不同于之前列出的。 64 位註冊表在**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\**子鍵中可用。 例如，.NET 框架 3.5 的註冊表子項**HKEY_LOCAL_MACHINE\\軟體\\\\Wow6432Node\\微軟\\NET\\框架設置 NDP v3.5**。

下面的示例查找 .NET 框架 1 到 4 個已安裝的版本：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>尋找 CLR 版本

與 .NET 框架一起安裝的 .NET 框架 CLR 是單獨版本。 有兩種方法可以檢測 .NET 框架 CLR 的版本：

- **Clrver.exe 工具**

  使用[CLR 版本工具 （Clrver.exe）](../tools/clrver-exe-clr-version-tool.md)確定電腦上安裝了 CLR 的哪些版本。 打開[視覺化工作室的開發人員命令提示符](../tools/developer-command-prompt-for-vs.md)並輸入`clrver`。

  範例輸出：

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **類`Environment`**

  > [!IMPORTANT]
  > 對於 .NET 框架 4.5 和更高版本，不要<xref:System.Environment.Version%2A?displayProperty=nameWithType>使用 屬性來檢測 CLR 的版本。 相反，查詢註冊表，如檢測[.NET 框架 4.5 和更高版本中所述](#detect-net-framework-45-and-later-versions)。
  
  01. 查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。
  
      傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。 它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。
  
      對於 .NET Framework 版本 4、4.5、4.5.1 和 4.5.2，返回<xref:System.Version>物件的字串表示形式為 4.0.30319。*xxxxx，**其中xxxxx*小於42000。 對於 .NET 框架 4.6 和更高版本，它有 4.0.30319.42000 的形式。
  
  01. 獲得**Version**物件後，按如下方式查詢它：
  
      - 針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。
  
      - 針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。
  
      - 針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。 這個方法會傳回單一值，其反映執行程式碼的執行階段版本。 它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。

  下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>另請參閱

- [如何：確定安裝了哪些 .NET 框架更新](how-to-determine-which-net-framework-updates-are-installed.md)
- [安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)
- [.NET 框架版本和依賴項](versions-and-dependencies.md)
