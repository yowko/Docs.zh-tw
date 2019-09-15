---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997569"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop 現會進行 IAgileObject 的 QueryInterface 作業 (WinRT 介面)

|   |   |
|---|---|
|詳細資料|從 .NET Framework 4.8 開始，當您搭配使用 WinRT 事件與 .NET 委派時，Windows 會進行 IAgileObject 的 QI 作業。  在舊版 .NET Framework 中，執行階段會讓該 QI 失敗，而無法訂閱此事件。<ul><li>[ x ] Quirked</li></ul>|
|建議|如果啟用 IAgileObject 的 QI 作業會導致執行中斷，您可以進行下列設定來停用此程式碼。 <h4>方法1：環境變數</h4> 設定下列環境變數：COMPLUS_DisableCCWSupportIAgileObject=1 這個方法會影響任何繼承此環境變數的環境。 這可能只是單一的主控台會話，如果您設定全域環境變數，它可能會影響整部電腦。 環境變數名稱不區分大小寫。 <h4>方法2：登錄</h4> 使用登錄編輯程式 (regedit.exe)，找出下列子機碼：HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFramework 然後新增下列項目：值名稱：DisableCCWSupportIAgileObject 類型：DWORD (32 位元) 值 (也稱為 REG_WORD) 值：1 您可以使用 Windows REG.EXE 工具，透過命令列或指令碼環境新增此值。 例如：<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>此案例會使用 <code>HKLM</code>，而不是 <code>HKEY_LOCAL_MACHINE</code>。 使用<code>reg add /?</code>來查看此語法的說明。 登錄值名稱不區分大小寫。|
|`Scope`|Edge|
|Version|4.8|
|類型|執行階段|
