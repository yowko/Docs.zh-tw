---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620000"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="81e2b-101">SqlBulkCopy 針對字串使用目的地資料行編碼方式</span><span class="sxs-lookup"><span data-stu-id="81e2b-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="81e2b-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="81e2b-102">Details</span></span>

<span data-ttu-id="81e2b-103">將資料插入資料行時，<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 會使用目的地資料行的編碼方式，而不是 <code>VARCHAR</code> 和 <code>CHAR</code> 類型的預設編碼方式。</span><span class="sxs-lookup"><span data-stu-id="81e2b-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="81e2b-104">這項變更可排除當目的地資料行未使用預設編碼方式時，使用預設編碼方式可能造成的資料損毀。</span><span class="sxs-lookup"><span data-stu-id="81e2b-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="81e2b-105">在某些鮮少發生的情況下，如果變更編碼方式後產生的資料太大而不適用於目的地資料行，現有的應用程式可能會擲回 SqlException 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="81e2b-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="81e2b-106">建議</span><span class="sxs-lookup"><span data-stu-id="81e2b-106">Suggestion</span></span>

<span data-ttu-id="81e2b-107">由於編碼方式的差異，預期 <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> 不會再損毀資料。</span><span class="sxs-lookup"><span data-stu-id="81e2b-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="81e2b-108">如果所複製的字串接近目的地資料行的大小限制，可能必須預先編碼資料 (要複製以確認資料可納入目的地資料行) 或攔截 <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="81e2b-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="81e2b-109">名稱</span><span class="sxs-lookup"><span data-stu-id="81e2b-109">Name</span></span>    | <span data-ttu-id="81e2b-110">值</span><span class="sxs-lookup"><span data-stu-id="81e2b-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="81e2b-111">影響範圍</span><span class="sxs-lookup"><span data-stu-id="81e2b-111">Scope</span></span>   |<span data-ttu-id="81e2b-112">Edge</span><span class="sxs-lookup"><span data-stu-id="81e2b-112">Edge</span></span>|
|<span data-ttu-id="81e2b-113">版本</span><span class="sxs-lookup"><span data-stu-id="81e2b-113">Version</span></span>|<span data-ttu-id="81e2b-114">4.5</span><span class="sxs-lookup"><span data-stu-id="81e2b-114">4.5</span></span>|
|<span data-ttu-id="81e2b-115">類型</span><span class="sxs-lookup"><span data-stu-id="81e2b-115">Type</span></span>|<span data-ttu-id="81e2b-116">執行階段</span><span class="sxs-lookup"><span data-stu-id="81e2b-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81e2b-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="81e2b-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
