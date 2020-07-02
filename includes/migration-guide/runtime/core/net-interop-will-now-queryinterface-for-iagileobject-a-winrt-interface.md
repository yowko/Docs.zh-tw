---
ms.openlocfilehash: 150b94b55fa8f2a29f1da7cf7ac7bf6dd06b9666
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621948"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop 現會進行 IAgileObject 的 QueryInterface 作業 (WinRT 介面)

#### <a name="details"></a>詳細資料

從 .NET Framework 4.8 開始，當您搭配使用 WinRT 事件與 .NET 委派時，Windows 會進行 IAgileObject 的 QI 作業。  在舊版 .NET Framework 中，執行階段會讓該 QI 失敗，而無法訂閱此事件。<ul><li>[ x ] Quirked</li></ul>

#### <a name="suggestion"></a>建議

如果啟用 IAgileObject 的 QI 作業會導致執行中斷，您可以進行下列設定來停用此程式碼。 <h4>方法1：環境變數</h4> 設定下列環境變數：COMPLUS_DisableCCWSupportIAgileObject=1 這個方法會影響任何繼承此環境變數的環境。 這可能只是單一的主控台會話，如果您設定全域環境變數，它可能會影響整部電腦。 環境變數名稱不區分大小寫。 <h4>方法2：登錄</h4> 使用 [登錄編輯程式] （regedit.exe），尋找下列其中一個子機碼： HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen 新增下列內容：值名稱： DisableCCWSupportIAgileObject 類型： DWORD （32位）值（也稱為 REG_WORD）值：1You 可以使用 Windows REG.EXE 工具，從命令列或腳本環境新增此值。 例如：<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>此案例會使用 <code>HKLM</code>，而不是 <code>HKEY_LOCAL_MACHINE</code>。 使用 <code>reg add /?</code> 來查看此語法的說明。 登錄值名稱不區分大小寫。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.8|
|類型|執行階段|
