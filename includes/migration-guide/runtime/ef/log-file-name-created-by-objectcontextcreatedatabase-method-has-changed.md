---
ms.openlocfilehash: 768a948849064cedb38110f5ed271717442325c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620019"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="25367-101">ObjectContext.CreateDatabase 方法所建立的記錄檔名稱已變更為符合 SQL Server 規格</span><span class="sxs-lookup"><span data-stu-id="25367-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

#### <a name="details"></a><span data-ttu-id="25367-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="25367-102">Details</span></span>

<span data-ttu-id="25367-103">無論是直接呼叫 <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> 方法，或在連接字串中使用 Code First 搭配 SqlClient 提供者和 AttachDBFilename 值進行呼叫，該方法都會建立名為 filename_log.ldf 的記錄檔，而不是 filename.ldf (其中 filename 是 AttachDBFilename 值所指定的檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="25367-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=fullName> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="25367-104">這項變更可透過提供依據 SQL Server 規格命名的記錄檔改善偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="25367-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25367-105">建議</span><span class="sxs-lookup"><span data-stu-id="25367-105">Suggestion</span></span>

<span data-ttu-id="25367-106">如果記錄檔名稱對應用程式很重要，則應更新應用程式以採用標準 _log.ldf 檔案名稱格式。</span><span class="sxs-lookup"><span data-stu-id="25367-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>

| <span data-ttu-id="25367-107">名稱</span><span class="sxs-lookup"><span data-stu-id="25367-107">Name</span></span>    | <span data-ttu-id="25367-108">值</span><span class="sxs-lookup"><span data-stu-id="25367-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25367-109">影響範圍</span><span class="sxs-lookup"><span data-stu-id="25367-109">Scope</span></span>   |<span data-ttu-id="25367-110">Edge</span><span class="sxs-lookup"><span data-stu-id="25367-110">Edge</span></span>|
|<span data-ttu-id="25367-111">版本</span><span class="sxs-lookup"><span data-stu-id="25367-111">Version</span></span>|<span data-ttu-id="25367-112">4.5</span><span class="sxs-lookup"><span data-stu-id="25367-112">4.5</span></span>|
|<span data-ttu-id="25367-113">類型</span><span class="sxs-lookup"><span data-stu-id="25367-113">Type</span></span>|<span data-ttu-id="25367-114">執行階段</span><span class="sxs-lookup"><span data-stu-id="25367-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25367-115">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="25367-115">Affected APIs</span></span>

-<xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
