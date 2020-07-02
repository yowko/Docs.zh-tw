---
ms.openlocfilehash: a1db9916c69c5974191eb6108fb54a0d9ff060d2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622036"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a>SqlConnection.Open 在有非 IFS Winsock BSP 或 LSP 的 Windows 7 上會失敗

#### <a name="details"></a>詳細資料

在 .NET Framework 4.5 中，如果 <xref:System.Data.SqlClient.SqlConnection.Open> 和 <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> 在 Windows 7 電腦上執行，而且該電腦上有非 IFS Winsock BSP 或 LSP，則會失敗。若要判斷是否已安裝非 IFS BSP 或 LSP，請使用 <code>netsh WinSock Show Catalog</code> 命令，並檢查每個傳回的 <code>Winsock Catalog Provider Entry</code> 項目。 如果服務旗標值已設定 <code>0x20000</code> 位元，提供者會使用 IFS 控制代碼並將正常運作。 如果 <code>0x20000</code> 位元已清除 (未設定)，就是非 IFS BSP 或 LSP。

#### <a name="suggestion"></a>建議

此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。 或者，您也可以移除任何安裝的非 IFS Winsock LSP 來避免此錯誤 (bug)。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Minor|
|版本|4.5|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType></li></ul>|
