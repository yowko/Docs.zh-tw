---
title: "如何：將資料加入至剪貼簿"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 452dfc5a9645e8f43ab583099deec60faa2d1b4d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="b3ec7-102">如何：將資料加入至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="b3ec7-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="b3ec7-103"><xref:System.Windows.Forms.Clipboard>類別提供可用來與 Windows 作業系統的剪貼簿功能互動的方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="b3ec7-104">許多應用程式的資料做為暫存的儲存機制使用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="b3ec7-105">例如，文書處理器會使用剪貼簿剪下和貼上作業期間。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="b3ec7-106">也適用於將資料傳送到另一個應用程式從剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="b3ec7-107">當您將資料加入到剪貼簿時，您可以使其他應用程式可以辨識的資料，可以使用該格式表示的資料格式。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="b3ec7-108">此外，您也可以將資料加入至剪貼簿中，多個不同的格式，可能可以使用這些資料的其他應用程式數目增加。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="b3ec7-109">剪貼簿格式是字串，識別的格式，以便使用該格式的應用程式可以擷取相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="b3ec7-110"><xref:System.Windows.Forms.DataFormats>類別會提供貴用戶使用的預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="b3ec7-111">您也可以使用您自己的格式名稱，或使用物件的類型作為其格式。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="b3ec7-112">若要將資料加入至剪貼簿中一或多個格式，使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="b3ec7-113">您可以將任何物件傳遞至這個方法，但若要加入以多種格式的資料，您必須先將資料加入設計用於多種格式的個別物件。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="b3ec7-114">一般而言，您將加入您的資料<xref:System.Windows.Forms.DataObject>，但是您可以使用實作的任何類型<xref:System.Windows.Forms.IDataObject>介面。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="b3ec7-115">在[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]，您可以將資料直接加入剪貼簿使用設計來簡化基本剪貼簿工作的新方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="b3ec7-116">當您使用單一、 共同的格式，例如文字的資料時，請使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3ec7-117">所有的 Windows 應用程式共用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="b3ec7-118">因此，內容可能會變更當您切換到另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="b3ec7-119"><xref:System.Windows.Forms.Clipboard>類別只可以用於設定為單一執行緒 apartment (STA) 模式的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="b3ec7-120">若要使用這個類別，請確認您`Main`方法標示為<xref:System.STAThreadAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="b3ec7-121">物件必須可序列化，才能放在剪貼簿上。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="b3ec7-122">若要讓型別能夠進行序列化，將它與標記<xref:System.SerializableAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="b3ec7-123">如果您將不可序列化的物件傳遞至剪貼簿方法時，該方法會失敗而不擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="b3ec7-124">如需序列化的詳細資訊，請參閱 <xref:System.Runtime.Serialization>。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="b3ec7-125">若要將資料加入至剪貼簿中單一的一般格式</span><span class="sxs-lookup"><span data-stu-id="b3ec7-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="b3ec7-126">使用<xref:System.Windows.Forms.Clipboard.SetAudio%2A>， <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.SetImage%2A>，或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="b3ec7-127">這些方法都只[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="b3ec7-128">若要將資料加入至剪貼簿中的自訂格式</span><span class="sxs-lookup"><span data-stu-id="b3ec7-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="b3ec7-129">使用<xref:System.Windows.Forms.Clipboard.SetData%2A>方法以自訂的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="b3ec7-130">這個方法是僅適用於[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="b3ec7-131">您也可以使用具有預先定義的格式名稱<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="b3ec7-132">如需詳細資訊，請參閱<xref:System.Windows.Forms.DataFormats>。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="b3ec7-133">若要將資料加入至剪貼簿以多種格式</span><span class="sxs-lookup"><span data-stu-id="b3ec7-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="b3ec7-134">使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法並傳入<xref:System.Windows.Forms.DataObject>，其中包含您的資料。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="b3ec7-135">您必須使用這個方法將資料加入至剪貼簿上的版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3ec7-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="b3ec7-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="b3ec7-136">See Also</span></span>  
 [<span data-ttu-id="b3ec7-137">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="b3ec7-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="b3ec7-138">操作說明：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="b3ec7-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
