---
ms.openlocfilehash: cf1a8169351e29c18d85303fb32d4394877448f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803530"
---
### <a name="log-file-name-created-by-the-objectcontextcreatedatabase-method-has-changed-to-match-sql-server-specifications"></a><span data-ttu-id="52bf1-101">ObjectContext.CreateDatabase 方法所建立的記錄檔名稱已變更為符合 SQL Server 規格</span><span class="sxs-lookup"><span data-stu-id="52bf1-101">Log file name created by the ObjectContext.CreateDatabase method has changed to match SQL Server specifications</span></span>

|   |   |
|---|---|
|<span data-ttu-id="52bf1-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="52bf1-102">Details</span></span>|<span data-ttu-id="52bf1-103">無論是直接呼叫 <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> 方法，或在連接字串中使用 Code First 搭配 SqlClient 提供者和 AttachDBFilename 值進行呼叫，該方法都會建立名為 filename_log.ldf 的記錄檔，而不是 filename.ldf (其中 filename 是 AttachDBFilename 值所指定的檔案名稱)。</span><span class="sxs-lookup"><span data-stu-id="52bf1-103">When the <xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=name> method is called either directly or by using Code First with the SqlClient provider and an AttachDBFilename value in the connection string, it creates a log file named filename_log.ldf instead of filename.ldf (where filename is the name of the file specified by the AttachDBFilename value).</span></span> <span data-ttu-id="52bf1-104">這項變更可透過提供依據 SQL Server 規格命名的記錄檔改善偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="52bf1-104">This change improves debugging by providing a log file named according to SQL Server specifications.</span></span>|
|<span data-ttu-id="52bf1-105">建議</span><span class="sxs-lookup"><span data-stu-id="52bf1-105">Suggestion</span></span>|<span data-ttu-id="52bf1-106">如果記錄檔名稱對應用程式很重要，則應更新應用程式以採用標準 _log.ldf 檔案名稱格式。</span><span class="sxs-lookup"><span data-stu-id="52bf1-106">If the log file name is important for an app, the app should be updated to expect the standard _log.ldf file name format.</span></span>|
|<span data-ttu-id="52bf1-107">範圍</span><span class="sxs-lookup"><span data-stu-id="52bf1-107">Scope</span></span>|<span data-ttu-id="52bf1-108">Edge</span><span class="sxs-lookup"><span data-stu-id="52bf1-108">Edge</span></span>|
|<span data-ttu-id="52bf1-109">版本</span><span class="sxs-lookup"><span data-stu-id="52bf1-109">Version</span></span>|<span data-ttu-id="52bf1-110">4.5</span><span class="sxs-lookup"><span data-stu-id="52bf1-110">4.5</span></span>|
|<span data-ttu-id="52bf1-111">類型</span><span class="sxs-lookup"><span data-stu-id="52bf1-111">Type</span></span>|<span data-ttu-id="52bf1-112">執行階段</span><span class="sxs-lookup"><span data-stu-id="52bf1-112">Runtime</span></span>|
|<span data-ttu-id="52bf1-113">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="52bf1-113">Affected APIs</span></span>|<ul><li><xref:System.Data.Objects.ObjectContext.CreateDatabase?displayProperty=nameWithType></li></ul>|
