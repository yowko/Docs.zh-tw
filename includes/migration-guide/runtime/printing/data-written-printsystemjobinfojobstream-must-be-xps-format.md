---
ms.openlocfilehash: 19be8a7755d9b238ab6507eaa73319bddf39faa3
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497678"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="53835-101">寫入 PrintSystemJobInfo.JobStream 的資料必須是 XPS 格式</span><span class="sxs-lookup"><span data-stu-id="53835-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="53835-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="53835-102">Details</span></span>

<span data-ttu-id="53835-103"><xref:System.Printing.PrintSystemJobInfo.JobStream> 屬性會公開列印工作的資料流。</span><span class="sxs-lookup"><span data-stu-id="53835-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="53835-104">使用者可藉由寫入此資料流，將原始資料傳送至基礎作業系統列印元件。從 Windows 8 和更新版本的 Windows 作業系統上的 .NET Framework 4.5 開始，寫入此資料流的資料必須是作為套件資料流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="53835-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="53835-105">建議</span><span class="sxs-lookup"><span data-stu-id="53835-105">Suggestion</span></span>

<span data-ttu-id="53835-106">若要輸出列印的內容，您可以執行下列任何一項操作：</span><span class="sxs-lookup"><span data-stu-id="53835-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="53835-107">使用 <xref:System.Windows.Xps.XpsDocumentWriter> 類別來輸出列印的內容。</span><span class="sxs-lookup"><span data-stu-id="53835-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="53835-108">這是建議的替代方案。</span><span class="sxs-lookup"><span data-stu-id="53835-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="53835-109">請確定傳送至 <xref:System.Printing.PrintSystemJobInfo.JobStream> 屬性所傳回之資料流的資料是作為套件資料流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="53835-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="53835-110">名稱</span><span class="sxs-lookup"><span data-stu-id="53835-110">Name</span></span>    | <span data-ttu-id="53835-111">值</span><span class="sxs-lookup"><span data-stu-id="53835-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="53835-112">範圍</span><span class="sxs-lookup"><span data-stu-id="53835-112">Scope</span></span>   |<span data-ttu-id="53835-113">Minor</span><span class="sxs-lookup"><span data-stu-id="53835-113">Minor</span></span>|
|<span data-ttu-id="53835-114">版本</span><span class="sxs-lookup"><span data-stu-id="53835-114">Version</span></span>|<span data-ttu-id="53835-115">4.5</span><span class="sxs-lookup"><span data-stu-id="53835-115">4.5</span></span>|
|<span data-ttu-id="53835-116">類型</span><span class="sxs-lookup"><span data-stu-id="53835-116">Type</span></span>|<span data-ttu-id="53835-117">執行階段</span><span class="sxs-lookup"><span data-stu-id="53835-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="53835-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="53835-118">Affected APIs</span></span>

- <xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Printing.PrintSystemJobInfo.JobStream`

-->
