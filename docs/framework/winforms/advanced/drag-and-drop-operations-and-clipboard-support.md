---
title: "拖放作業和剪貼簿支援"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drag and drop [Windows Forms]
- drag and drop [Windows Forms], Windows Forms
- Clipboard [Windows Forms], Windows Forms
ms.assetid: 7cce79b6-5835-46fd-b690-73f12ad368b2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 722c37645d95009ce03bbbf813bc9f9fb2418e60
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="drag-and-drop-operations-and-clipboard-support"></a><span data-ttu-id="37d47-102">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="37d47-102">Drag-and-Drop Operations and Clipboard Support</span></span>
<span data-ttu-id="37d47-103">若要在 Windows 架構應用程式內啟用使用者拖放作業，您可以處理一系列的事件，最值得注意的是 <xref:System.Windows.Forms.Control.DragEnter>、<xref:System.Windows.Forms.Control.DragLeave> 和 <xref:System.Windows.Forms.Control.DragDrop> 事件。</span><span class="sxs-lookup"><span data-stu-id="37d47-103">You can enable user drag-and-drop operations within a Windows-based application by handling a series of events, most notably the <xref:System.Windows.Forms.Control.DragEnter>, <xref:System.Windows.Forms.Control.DragLeave>, and <xref:System.Windows.Forms.Control.DragDrop> events.</span></span>  
  
 <span data-ttu-id="37d47-104">您也可以使用簡單的方法呼叫，將使用者剪下/複製/貼上支援和使用者資料傳輸實作至 Windows 架構應用程式中的剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="37d47-104">You can also implement user cut/copy/paste support and user data transfer to the Clipboard within your Windows-based applications by using simple method calls.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="37d47-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="37d47-105">In This Section</span></span>  
 [<span data-ttu-id="37d47-106">逐步解說：在 Windows Forms 中執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="37d47-106">Walkthrough: Performing a Drag-and-Drop Operation in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)  
 <span data-ttu-id="37d47-107">說明如何開始拖放作業。</span><span class="sxs-lookup"><span data-stu-id="37d47-107">Explains how to start a drag-and-drop operation.</span></span>  
  
 [<span data-ttu-id="37d47-108">操作說明：在應用程式間執行拖放作業</span><span class="sxs-lookup"><span data-stu-id="37d47-108">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 <span data-ttu-id="37d47-109">說明如何跨應用程式完成拖放作業。</span><span class="sxs-lookup"><span data-stu-id="37d47-109">Illustrates how to accomplish drag-and-drop operations across applications.</span></span>  
  
 [<span data-ttu-id="37d47-110">操作說明：將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="37d47-110">How to: Add Data to the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 <span data-ttu-id="37d47-111">說明如何以程式設計方式，在剪貼簿上插入資訊。</span><span class="sxs-lookup"><span data-stu-id="37d47-111">Describes a way to programmatically insert information on the Clipboard.</span></span>  
  
 [<span data-ttu-id="37d47-112">操作說明：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="37d47-112">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 <span data-ttu-id="37d47-113">說明如何存取儲存在剪貼簿上的資料。</span><span class="sxs-lookup"><span data-stu-id="37d47-113">Describes how to access the data stored on the Clipboard.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="37d47-114">相關章節</span><span class="sxs-lookup"><span data-stu-id="37d47-114">Related Sections</span></span>  
 [<span data-ttu-id="37d47-115">Windows Forms 中的拖放功能</span><span class="sxs-lookup"><span data-stu-id="37d47-115">Drag-and-Drop Functionality in Windows Forms</span></span>](../../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)  
 <span data-ttu-id="37d47-116">說明用來實作拖放行為的方法、事件和類別。</span><span class="sxs-lookup"><span data-stu-id="37d47-116">Describes the methods, events, and classes used to implement drag-and-drop behavior.</span></span>  
  
 <xref:System.Windows.Forms.Control.QueryContinueDrag>  
 <span data-ttu-id="37d47-117">說明要求權限以繼續拖曳作業之事件的複雜性。</span><span class="sxs-lookup"><span data-stu-id="37d47-117">Describes the intricacies of the event that asks permission to continue the drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Control.DoDragDrop%2A>  
 <span data-ttu-id="37d47-118">說明開始拖曳作業之主要方法的複雜性。</span><span class="sxs-lookup"><span data-stu-id="37d47-118">Describes the intricacies of the method that is central to beginning a drag operation.</span></span>  
  
 <xref:System.Windows.Forms.Clipboard>  
 <span data-ttu-id="37d47-119">另請參閱[如何： 傳送資料至作用中 MDI 子系](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\))。</span><span class="sxs-lookup"><span data-stu-id="37d47-119">Also see [How to: Send Data to the Active MDI Child](http://msdn.microsoft.com/library/y0hkh2c8\(v=vs.110\)).</span></span>
