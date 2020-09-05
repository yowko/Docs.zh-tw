---
ms.openlocfilehash: 9ab1686f60bcdbfef5f18576be17aee8c931f9aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497462"
---
### <a name="sqlconnectionopen-fails-on-windows-7-with-non-ifs-winsock-bsp-or-lsp-present"></a><span data-ttu-id="7eb96-101">SqlConnection.Open 在有非 IFS Winsock BSP 或 LSP 的 Windows 7 上會失敗</span><span class="sxs-lookup"><span data-stu-id="7eb96-101">SqlConnection.Open fails on Windows 7 with non-IFS Winsock BSP or LSP present</span></span>

#### <a name="details"></a><span data-ttu-id="7eb96-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7eb96-102">Details</span></span>

<span data-ttu-id="7eb96-103">在 .NET Framework 4.5 中，如果 <xref:System.Data.SqlClient.SqlConnection.Open> 和 <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> 在 Windows 7 電腦上執行，而且該電腦上有非 IFS Winsock BSP 或 LSP，則會失敗。若要判斷是否已安裝非 IFS BSP 或 LSP，請使用 <code>netsh WinSock Show Catalog</code> 命令，並檢查每個傳回的 <code>Winsock Catalog Provider Entry</code> 項目。</span><span class="sxs-lookup"><span data-stu-id="7eb96-103"><xref:System.Data.SqlClient.SqlConnection.Open> and <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)> fail in the .NET Framework 4.5 if running on a Windows 7 machine with a non-IFS Winsock BSP or LSP are present on the computer.To determine whether a non-IFS BSP or LSP is installed, use the <code>netsh WinSock Show Catalog</code> command, and examine every <code>Winsock Catalog Provider Entry</code> item that is returned.</span></span> <span data-ttu-id="7eb96-104">如果服務旗標值已設定 <code>0x20000</code> 位元，提供者會使用 IFS 控制代碼並將正常運作。</span><span class="sxs-lookup"><span data-stu-id="7eb96-104">If the Service Flags value has the <code>0x20000</code> bit set, the provider uses IFS handles and will work correctly.</span></span> <span data-ttu-id="7eb96-105">如果 <code>0x20000</code> 位元已清除 (未設定)，就是非 IFS BSP 或 LSP。</span><span class="sxs-lookup"><span data-stu-id="7eb96-105">If the <code>0x20000</code> bit is clear (not set), it is a non-IFS BSP or LSP.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7eb96-106">建議</span><span class="sxs-lookup"><span data-stu-id="7eb96-106">Suggestion</span></span>

<span data-ttu-id="7eb96-107">此錯誤 (bug) 在 .NET Framework 4.5.2 中已修正，因此可藉由升級 .NET Framework 來避免。</span><span class="sxs-lookup"><span data-stu-id="7eb96-107">This bug has been fixed in the .NET Framework 4.5.2, so it can be avoided by upgrading the .NET Framework.</span></span> <span data-ttu-id="7eb96-108">或者，您也可以移除任何安裝的非 IFS Winsock LSP 來避免此錯誤 (bug)。</span><span class="sxs-lookup"><span data-stu-id="7eb96-108">Alternatively, it can be avoided by removing any installed non-IFS Winsock LSPs.</span></span>

| <span data-ttu-id="7eb96-109">名稱</span><span class="sxs-lookup"><span data-stu-id="7eb96-109">Name</span></span>    | <span data-ttu-id="7eb96-110">值</span><span class="sxs-lookup"><span data-stu-id="7eb96-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7eb96-111">範圍</span><span class="sxs-lookup"><span data-stu-id="7eb96-111">Scope</span></span>   |<span data-ttu-id="7eb96-112">Minor</span><span class="sxs-lookup"><span data-stu-id="7eb96-112">Minor</span></span>|
|<span data-ttu-id="7eb96-113">版本</span><span class="sxs-lookup"><span data-stu-id="7eb96-113">Version</span></span>|<span data-ttu-id="7eb96-114">4.5</span><span class="sxs-lookup"><span data-stu-id="7eb96-114">4.5</span></span>|
|<span data-ttu-id="7eb96-115">類型</span><span class="sxs-lookup"><span data-stu-id="7eb96-115">Type</span></span>|<span data-ttu-id="7eb96-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="7eb96-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="7eb96-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7eb96-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlConnection.Open?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Data.SqlClient.SqlConnection.Open`
- `M:System.Data.SqlClient.SqlConnection.OpenAsync(System.Threading.CancellationToken)`

-->
