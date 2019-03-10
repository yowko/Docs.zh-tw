---
title: 拖放作業和剪貼簿支援
ms.date: 03/30/2017
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
ms.openlocfilehash: 5e7bb75b648163dab7e410a159d55ebbb75f1b0a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711742"
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="a60c2-102">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="a60c2-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="a60c2-103">若要在 Windows 架構應用程式內啟用使用者拖放作業，您可以處理一系列的事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。</span><span class="sxs-lookup"><span data-stu-id="a60c2-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="a60c2-104">您也可以使用簡單的方法呼叫，將使用者剪下/複製/貼上支援和使用者資料傳輸實作至 Windows 架構應用程式中的剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="a60c2-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a60c2-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="a60c2-105">In This Section</span></span>  
 [<span data-ttu-id="a60c2-106">逐步解說：在 Windows Form 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="a60c2-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="a60c2-107">說明如何開始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="a60c2-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="a60c2-108">如何：執行應用程式之間的拖放作業</span><span class="sxs-lookup"><span data-stu-id="a60c2-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="a60c2-109">說明如何跨應用程式完成拖放作業。</span><span class="sxs-lookup"><span data-stu-id="a60c2-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="a60c2-110">如何：將資料加入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="a60c2-110">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="a60c2-111">說明如何以程式設計方式，在剪貼簿上插入資訊。</span><span class="sxs-lookup"><span data-stu-id="a60c2-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="a60c2-112">如何：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="a60c2-112">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="a60c2-113">說明如何存取儲存在剪貼簿上的資料。</span><span class="sxs-lookup"><span data-stu-id="a60c2-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a60c2-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="a60c2-114">Related Sections</span></span>  
 [<span data-ttu-id="a60c2-115">Windows Forms 中的拖放功能</span><span class="sxs-lookup"><span data-stu-id="a60c2-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="a60c2-116">說明用來實作拖放行為的方法、事件和類別。</span><span class="sxs-lookup"><span data-stu-id="a60c2-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="a60c2-117">說明要求權限以繼續拖曳作業之事件的複雜性。</span><span class="sxs-lookup"><span data-stu-id="a60c2-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="a60c2-118">說明開始拖曳作業之主要方法的複雜性。</span><span class="sxs-lookup"><span data-stu-id="a60c2-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="a60c2-119">另請參閱[How to:將資料傳送至作用中的 MDI 子系](how-to-send-data-to-the-active-mdi-child.md)。</span><span class="sxs-lookup"><span data-stu-id="a60c2-119">Also see [How to: Send Data to the Active MDI Child](how-to-send-data-to-the-active-mdi-child.md).</span></span>
