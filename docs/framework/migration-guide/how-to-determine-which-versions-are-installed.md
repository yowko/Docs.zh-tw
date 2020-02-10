---
title: 判斷安裝的 .NET Framework 版本
description: 藉由查詢 Windows 登錄，使用程式碼、regedit.exe 或 PowerShell 來偵測電腦上所安裝的 .NET Framework 版本。
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
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093823"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>如何：判斷安裝的 .NET Framework 版本

使用者可以在電腦上[安裝](../install/index.md)及執行多個版本的 .NET Framework。 當您開發或部署應用程式時，您可能需要知道使用者電腦上安裝的 .NET Framework 版本。 登錄包含電腦上安裝的 .NET Framework 版本清單。

.NET Framework 包含兩個主要元件，各有各的版本控制：

- 組件集合，這是為應用程式提供功能的類型與資源集合。 .NET Framework 和組件會共用相同的版本號碼。 例如，.NET Framework 版本包含 4.5、4.6.1 和 4.7.2。

- 通用語言執行平台 (CLR)，負責管理和執行應用程式的程式碼。 單一的 CLR 版本通常會支援多個 .NET Framework 版本。 例如，CLR 版本4.0.30319。*xxxxx，其中* *xxxxx*小於42000，支援 .NET Framework 版本4到4.5.2。 CLR 版本大於或等於4.0.30319.42000 支援從 .NET Framework 4.6 開始的 .NET Framework 版本。

有提供社區維護的工具可協助您偵測已安裝的 .NET Framework 版本：

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  .NET 2.0 命令列工具。

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  PowerShell 2.0 模組。

如需偵測每個 .NET Framework 版本之已安裝更新的詳細資訊，請參閱[如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)。

## <a name="detect-net-framework-45-and-later-versions"></a>偵測 .NET Framework 4.5 和更新版本

安裝在電腦上的 .NET Framework 版本（4.5 和更新版本）列在登錄中**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\Full**。 如果遺漏**完整**的子機碼，則不會安裝 .NET Framework 4.5 或更新版本。

> [!NOTE]
> 登錄路徑中的**NET Framework 安裝程式**子機碼*不*是以句號開頭。

登錄中的**Release** REG_DWORD 值代表已安裝 .NET Framework 版本。

<a name="version_table"></a>

| .NET Framework 版本 | **發行**的值 |
| ---------------------- | -------------------------- |
| .NET Framework 4.5     | 所有 Windows 作業系統：378389 |
| .NET Framework 4.5.1   | 在 Windows 8.1 和 Windows Server 2012 R2 上：378675<br />在其他所有 Windows 作業系統上：378758 |
| .NET Framework 4.5.2   | 所有 Windows 作業系統：379893 |
| .NET Framework 4.6     | 在 Windows 10: 393295 上<br />在其他所有 Windows 作業系統上：393297 |
| .NET Framework 4.6.1   | Windows 10 11 月更新系統：394254<br />在所有其他 Windows 作業系統上（包括 Windows 10）：394271 |
| .NET Framework 4.6.2   | Windows 10 年度更新版及 Windows Server 2016：394802<br />在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：394806 |
| .NET Framework 4.7     | Windows 10 Creators Update：460798<br />在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：460805 |
| .NET Framework 4.7.1   | Windows 10 秋季建立者更新和 Windows Server，版本1709：461308<br/>在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：461310 |
| .NET Framework 4.7.2   | Windows 10 2018 年4月更新和 Windows Server，版本1803：461808<br/>在 Windows 10 2018 年4月更新和 Windows Server 的所有 Windows 作業系統上，版本1803：461814 |
| .NET Framework 4.8     | 在 Windows 10 5 月2019更新和 Windows 10 十一月2019更新：528040<br/>在 Windows 10 和 Windows Server 上，版本1909：528209<br/>在所有其他 Windows 作業系統（包括其他 Windows 10 作業系統）上：528049 |

### <a name="minimum-version"></a>最小版本

若要判斷 .NET Framework 的*最低*版本是否存在，請使用上表中該版本的最小**發行**REG_DWORD 值。

例如，如果您的應用程式是在 .NET Framework 4.8 或更新版本下執行，請測試**版本**REG_DWORD 值是否*大於或等於*528040。

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

    您必須具有系統管理認證才能執行 regedit。

01. 在 [登錄編輯程式] 中，開啟下列子機碼： **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\Full**。 如果 **Full** 子機碼不存在，即表示未安裝 .NET Framework 4.5 或更新版本。

01. 檢查名為**Release**的 REG_DWORD 專案。 如果已存在，則您已安裝 .NET Framework 4.5 或更新版本。 其值對應至特定版本的 .NET Framework。 例如，在下圖中， **release**專案的值是528040，也就是 .NET Framework 4.8 的發行金鑰。

    ![.NET Framework 4.5 的登錄專案](./media/clr-installdir.png ".NET Framework 4.5 的登錄專案")

### <a name="use-powershell-to-check-for-a-minimum-version"></a>使用 PowerShell 檢查最低版本

使用 PowerShell 命令來檢查 HKEY_LOCAL_MACHINE\\SOFTWARE 的**Release**專案值 **\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\Full**子機碼。

下列範例會檢查 **Release** 項目值，以判斷是否安裝了 .NET Framework 4.6.2 或更新版本。 如已安裝，則此程式碼會傳回 `True`；否則傳回 `False`。

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a>使用程式碼查詢登錄

01. 使用 <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 和 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 方法，在 Windows 登錄中存取**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\Full**子機碼。

    > [!IMPORTANT]
    > 如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 64位登錄適用于**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 子機碼。 例如，.NET Framework 4.5 的登錄子機碼**HKEY_LOCAL_MACHINE\\軟體\\Wow6432Node\\Microsoft\\NET Framework 安裝\\NDP\\v4\\Full**。

01. 檢查**Release** REG_DWORD 值以判斷已安裝的版本。 若要正向相容，請檢查是否有大於或等於 [.NET Framework 版本表](#version_table)中所列值的值。

下列範例會檢查登錄中的 **Release** 項目值，尋找已安裝的 .NET Framework 4.5 和更新版本：

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

此範例遵循版本檢查的建議做法：

- 它會檢查 **Release** 項目值是否「大於或等於」已知版本機碼的值。
- 它會從最新版本依序檢查到最舊版本。

## <a name="detect-net-framework-10-through-40"></a>偵測 .NET Framework 1.0 到4。0

從1.1 到4.0 的每個版本 .NET Framework 都會列為**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET Framework 安裝程式\\NDP**的子機碼。 下表列出每個 .NET Framework 版本的路徑。 對於大部分版本而言，`1` 的**安裝**REG_DWORD 值，表示已安裝此版本。 在這些子機碼中，還有一個**版本**REG_SZ 值，其中包含版本字串。

> [!NOTE]
> 登錄路徑中的**NET Framework 安裝程式**子機碼*不*是以句號開頭。

| Framework 版本  | 登錄子機碼 | 值 |
| ------------------ | --------------- | ----- |
| 1.0                | **HKLM\\Software\\Microsoft\\.Netframework\\原則\\v1.0\\3705**     | **安裝**REG_SZ 等於 `1` |
| 1.1                | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v 1.1.4322**   | **安裝**REG_DWORD 等於 `1` |
| 2.0                | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v 2.0.50727**  | **安裝**REG_DWORD 等於 `1` |
| 3.0                | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v3.0\\安裝程式** | **InstallSuccess**REG_DWORD 等於 `1` |
| 3.5                | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v 3。5**        | **安裝**REG_DWORD 等於 `1` |
| 4.0 用戶端設定檔 | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\用戶端**  | **安裝**REG_DWORD 等於 `1` |
| 4.0 完整設定檔   | **HKLM\\Software\\Microsoft\\NET Framework 安裝程式\\NDP\\v4\\Full**    | **安裝**REG_DWORD 等於 `1` |

> [!IMPORTANT]
> 如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 64位登錄適用于**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 子機碼。 例如，.NET Framework 3.5 的登錄子機碼為**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework 安裝程式\\NDP\\v 3.5**。

請注意，.NET Framework 1.0 子機碼的登錄路徑與其他子機碼不同。

### <a name="use-registry-editor-older-framework-versions"></a>使用登錄編輯程式（較舊的 framework 版本）

01. 從 [開始] 功能表上，選擇 [執行]，輸入 *regedit*，然後選取 [確定]。

    您必須具有系統管理認證才能執行 regedit。

01. 開啟與您要檢查之版本相符的子機碼。 使用 [偵測[.NET Framework 1.0 到 4.0](#detect-net-framework-10-through-40) ] 區段中的資料表。

    下圖顯示 .NET Framework 3.5 的子機碼及其**版本**值。

    ![.NET Framework 3.5 的登錄專案。](./media/net-4-and-earlier.png ".NET Framework 3.5 和更早版本")

### <a name="query-the-registry-using-code-older-framework-versions"></a>使用程式碼查詢登錄（較舊的 framework 版本）

使用 <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 類別來存取 Windows 登錄中的**HKEY_LOCAL_MACHINE\\軟體\\Microsoft\\NET Framework 安裝程式\\NDP**子機碼。

> [!IMPORTANT]
> 如果您執行的應用程式是32位且在64位 Windows 中執行，則登錄路徑會與先前所列的不同。 64位登錄適用于**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 子機碼。 例如，.NET Framework 3.5 的登錄子機碼為**HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework 安裝程式\\NDP\\v 3.5**。

下列範例會尋找已安裝的 .NET Framework 1 到4個版本：

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>尋找 CLR 版本

隨 .NET Framework 安裝的 .NET Framework CLR 會分別進行版本設定。 偵測 .NET Framework CLR 版本的方法有兩種：

- **Clrver .exe 工具**

  使用[Clr 版本工具（Clrver）](../tools/clrver-exe-clr-version-tool.md)來判斷電腦上安裝了哪些 CLR 版本。 開啟[Visual Studio 的開發人員命令提示字元](../tools/developer-command-prompt-for-vs.md)，然後輸入 `clrver`。

  範例輸出：

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- **`Environment` 類別**

  > [!IMPORTANT]
  > 若為 .NET Framework 4.5 和更新版本，請不要使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來偵測 CLR 的版本。 請改為查詢登錄，如偵測[.NET Framework 4.5 和更新版本](#detect-net-framework-45-and-later-versions)中所述。
  
  01. 查詢 <xref:System.Environment.Version?displayProperty=nameWithType> 屬性以擷取 <xref:System.Version> 物件。
  
      傳回的 `System.Version` 物件可識別目前執行程式碼的執行階段版本。 它不會傳回組件版本或已安裝在電腦上的其他執行階段版本。
  
      針對 .NET Framework 版本4、4.5、4.5.1 和4.5.2，傳回之 <xref:System.Version> 物件的字串表示格式為4.0.30319。*xxxxx*，其中*xxxxx*小於42000。 針對 .NET Framework 4.6 和更新版本，其格式為4.0.30319.42000。
  
  01. 在您擁有**版本**物件之後，請依照下列方式查詢它：
  
      - 針對主要版本識別項 (例如 4.0 版的 *4*)，請使用 <xref:System.Version.Major%2A?displayProperty=nameWithType> 屬性。
  
      - 針對次要版本識別項 (例如 4.0 版的 *0*)，請使用 <xref:System.Version.Minor%2A?displayProperty=nameWithType> 屬性。
  
      - 針對整個版本字串 (例如 *4.0.30319.18010*)，請使用 <xref:System.Version.ToString%2A?displayProperty=nameWithType> 方法。 這個方法會傳回單一值，其反映執行程式碼的執行階段版本。 它不會傳回組件版本或可能已安裝在電腦上的其他執行階段版本。

  下列範例使用 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 屬性來擷取 CLR 版本資訊：
  
  [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
  [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>另請參閱

- [如何：判斷已安裝的 .NET Framework 更新](how-to-determine-which-net-framework-updates-are-installed.md)
- [安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)
- [.NET Framework 版本和相依性](versions-and-dependencies.md)
