---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997569"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop 現會進行 IAgileObject 的 QueryInterface 作業 (WinRT 介面)

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.8 開始，當您搭配使用 WinRT 事件與 .NET 委派時，Windows 會進行 IAgileObject 的 QI 作業。  在舊版 .NET Framework 中，執行階段會讓該 QI 失敗，而無法訂閱此事件。<ul><li>[ x ] Quirked</li></ul>|
|建議|如果啟用 IAgileObject 的 QI 作業會導致執行中斷，您可以進行下列設定來停用此程式碼。 <h4>方法 1：環境變數</h4> 設定下列環境變數：COMPLUS_DisableCCWSupportIAgileObject=1 這個方法會影響任何繼承此環境變數的環境。 這可能只是單個主控台會話，或者如果全域設置環境變數，可能會影響整個電腦。 環境變數名稱不區分大小寫。 <h4>方法 2：註冊表</h4> 使用登錄編輯程式 （regedit.exe），查找以下任一子金鑰：HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft.NETFramework HKEY_CURRENT_USER_SOFTWARE.NETFramework，然後添加以下內容：值名稱：禁用CCWSupportIAgileObject類型：DWORD（32 位）值（也稱為REG_WORD）值：1 您可以使用 Windows REG。EXE 工具，用於從命令列或腳本環境添加此值。 例如：<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>此案例會使用 <code>HKLM</code>，而不是 <code>HKEY_LOCAL_MACHINE</code>。 用於<code>reg add /?</code>查看有關此語法的説明。 註冊表值名稱不區分大小寫。|
|影響範圍|Edge|
|版本|4.8|
|類型|執行階段|
