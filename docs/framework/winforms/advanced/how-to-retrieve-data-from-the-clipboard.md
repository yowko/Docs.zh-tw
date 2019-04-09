---
title: HOW TO：從剪貼簿擷取資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: aca110339c94afd5442aed5a2481964b456154f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201607"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a><span data-ttu-id="8ea19-102">HOW TO：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="8ea19-102">How to: Retrieve Data from the Clipboard</span></span>
<span data-ttu-id="8ea19-103"><xref:System.Windows.Forms.Clipboard>類別提供方法，您可以使用與 Windows 作業系統的剪貼簿功能互動。</span><span class="sxs-lookup"><span data-stu-id="8ea19-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="8ea19-104">許多應用程式資料做為暫存的儲存機制使用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8ea19-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="8ea19-105">例如，文書處理器使用剪貼簿剪下和貼上作業期間。</span><span class="sxs-lookup"><span data-stu-id="8ea19-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="8ea19-106">也適用於將資訊傳送到另一個應用程式從剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8ea19-106">The Clipboard is also useful for transferring information from one application to another.</span></span>  
  
 <span data-ttu-id="8ea19-107">有些應用程式會將資料儲存在剪貼簿中，多個格式增加可能可以使用這些資料的其他應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="8ea19-107">Some applications store data on the Clipboard in multiple formats to increase the number of other applications that can potentially use the data.</span></span> <span data-ttu-id="8ea19-108">剪貼簿格式會是識別格式的字串。</span><span class="sxs-lookup"><span data-stu-id="8ea19-108">A Clipboard format is a string that identifies the format.</span></span> <span data-ttu-id="8ea19-109">使用已識別的格式的應用程式可以擷取剪貼簿上相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="8ea19-109">An application that uses the identified format can retrieve the associated data on the Clipboard.</span></span> <span data-ttu-id="8ea19-110"><xref:System.Windows.Forms.DataFormats>類別會提供給您使用的預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="8ea19-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="8ea19-111">您也可以使用您自己的格式名稱，或使用物件的類型作為其格式。</span><span class="sxs-lookup"><span data-stu-id="8ea19-111">You can also use your own format names or use an object's type as its format.</span></span> <span data-ttu-id="8ea19-112">如需將資料加入至剪貼簿資訊，請參閱[How to:將資料加入至剪貼簿](how-to-add-data-to-the-clipboard.md)。</span><span class="sxs-lookup"><span data-stu-id="8ea19-112">For information about adding data to the Clipboard, see [How to: Add Data to the Clipboard](how-to-add-data-to-the-clipboard.md).</span></span>  
  
 <span data-ttu-id="8ea19-113">若要判斷 [剪貼簿] 是否包含以特定格式的資料，請使用其中一種`Contains`*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-113">To determine whether the Clipboard contains data in a particular format, use one of the `Contains`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="8ea19-114">若要從剪貼簿擷取資料，請使用其中一種`Get`*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-114">To retrieve data from the Clipboard, use one of the `Get`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="8ea19-115">這些方法會在新[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ea19-115">These methods are new in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
 <span data-ttu-id="8ea19-116">存取資料，從剪貼簿，使用版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]，使用<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>方法呼叫的方法傳回的<xref:System.Windows.Forms.IDataObject>。</span><span class="sxs-lookup"><span data-stu-id="8ea19-116">To access data from the Clipboard by using versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)], use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method and call the methods of the returned <xref:System.Windows.Forms.IDataObject>.</span></span> <span data-ttu-id="8ea19-117">若要判斷是否可傳回之物件中特定的格式，例如，呼叫<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-117">To determine whether a particular format is available in the returned object, for example, call the <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ea19-118">所有以 Windows 為基礎的應用程式共用系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="8ea19-118">All Windows-based applications share the system Clipboard.</span></span> <span data-ttu-id="8ea19-119">因此，內容會有所變更中是當您切換到另一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ea19-119">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="8ea19-120"><xref:System.Windows.Forms.Clipboard>類別只能設定為單一執行緒 apartment (STA) 模式的執行緒中。</span><span class="sxs-lookup"><span data-stu-id="8ea19-120">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="8ea19-121">若要使用這個類別，請確認您`Main`方法會標示<xref:System.STAThreadAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="8ea19-121">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="8ea19-122">若要從單一的常用格式剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="8ea19-122">To retrieve data from the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="8ea19-123">使用<xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>， <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.GetImage%2A>，或<xref:System.Windows.Forms.Clipboard.GetText%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-123">Use the <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, or <xref:System.Windows.Forms.Clipboard.GetText%2A> method.</span></span> <span data-ttu-id="8ea19-124">（選擇性） 使用 對應`Contains`*格式*方法，以判斷是否有特定的格式資料。</span><span class="sxs-lookup"><span data-stu-id="8ea19-124">Optionally, use the corresponding `Contains`*Format* methods first to determine whether data is available in a particular format.</span></span> <span data-ttu-id="8ea19-125">這些方法都只[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ea19-125">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a><span data-ttu-id="8ea19-126">從剪貼簿中的自訂格式，擷取資料</span><span class="sxs-lookup"><span data-stu-id="8ea19-126">To retrieve data from the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="8ea19-127">使用<xref:System.Windows.Forms.Clipboard.GetData%2A>方法以自訂格式名稱。</span><span class="sxs-lookup"><span data-stu-id="8ea19-127">Use the <xref:System.Windows.Forms.Clipboard.GetData%2A> method with a custom format name.</span></span> <span data-ttu-id="8ea19-128">這個方法是僅適用於[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ea19-128">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="8ea19-129">您也可以使用預先定義的格式名稱<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-129">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="8ea19-130">如需詳細資訊，請參閱<xref:System.Windows.Forms.DataFormats>。</span><span class="sxs-lookup"><span data-stu-id="8ea19-130">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a><span data-ttu-id="8ea19-131">若要從以多種格式剪貼簿 擷取資料</span><span class="sxs-lookup"><span data-stu-id="8ea19-131">To retrieve data from the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="8ea19-132">請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="8ea19-132">Use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method.</span></span> <span data-ttu-id="8ea19-133">您必須使用這個方法來擷取資料，從剪貼簿上的版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8ea19-133">You must use this method to retrieve data from the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="8ea19-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ea19-134">See also</span></span>

- [<span data-ttu-id="8ea19-135">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="8ea19-135">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
- [<span data-ttu-id="8ea19-136">HOW TO：將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="8ea19-136">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
