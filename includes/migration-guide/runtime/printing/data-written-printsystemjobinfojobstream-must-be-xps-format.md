---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803475"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="3a3c0-101">寫入 PrintSystemJobInfo.JobStream 的資料必須是 XPS 格式</span><span class="sxs-lookup"><span data-stu-id="3a3c0-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

|   |   |
|---|---|
|<span data-ttu-id="3a3c0-102">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a3c0-102">Details</span></span>|<span data-ttu-id="3a3c0-103"><xref:System.Printing.PrintSystemJobInfo.JobStream> 屬性會公開列印工作的資料流。</span><span class="sxs-lookup"><span data-stu-id="3a3c0-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="3a3c0-104">使用者可藉由寫入此資料流，將原始資料傳送至基礎作業系統列印元件。從 Windows 8 和更新版本的 Windows 作業系統上的 .NET Framework 4.5 開始，寫入此資料流的資料必須是作為套件資料流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="3a3c0-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>|
|<span data-ttu-id="3a3c0-105">建議</span><span class="sxs-lookup"><span data-stu-id="3a3c0-105">Suggestion</span></span>|<span data-ttu-id="3a3c0-106">若要輸出列印的內容，您可以執行下列任何一項操作：</span><span class="sxs-lookup"><span data-stu-id="3a3c0-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="3a3c0-107">使用 <xref:System.Windows.Xps.XpsDocumentWriter> 類別來輸出列印的內容。</span><span class="sxs-lookup"><span data-stu-id="3a3c0-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="3a3c0-108">這是建議的替代方案。</span><span class="sxs-lookup"><span data-stu-id="3a3c0-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="3a3c0-109">請確定傳送至 <xref:System.Printing.PrintSystemJobInfo.JobStream> 屬性所傳回之資料流的資料是作為套件資料流的 XPS 格式。</span><span class="sxs-lookup"><span data-stu-id="3a3c0-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>|
|<span data-ttu-id="3a3c0-110">範圍</span><span class="sxs-lookup"><span data-stu-id="3a3c0-110">Scope</span></span>|<span data-ttu-id="3a3c0-111">次要</span><span class="sxs-lookup"><span data-stu-id="3a3c0-111">Minor</span></span>|
|<span data-ttu-id="3a3c0-112">版本</span><span class="sxs-lookup"><span data-stu-id="3a3c0-112">Version</span></span>|<span data-ttu-id="3a3c0-113">4.5</span><span class="sxs-lookup"><span data-stu-id="3a3c0-113">4.5</span></span>|
|<span data-ttu-id="3a3c0-114">類型</span><span class="sxs-lookup"><span data-stu-id="3a3c0-114">Type</span></span>|<span data-ttu-id="3a3c0-115">執行階段</span><span class="sxs-lookup"><span data-stu-id="3a3c0-115">Runtime</span></span>|
|<span data-ttu-id="3a3c0-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3a3c0-116">Affected APIs</span></span>|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
