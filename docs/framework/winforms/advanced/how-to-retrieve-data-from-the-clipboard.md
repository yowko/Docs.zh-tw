---
title: 作法：從剪貼簿擷取資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: ca24615049abcc145698c033f31e6c98a38253bf
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040573"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a><span data-ttu-id="84f03-102">作法：從剪貼簿擷取資料</span><span class="sxs-lookup"><span data-stu-id="84f03-102">How to: Retrieve Data from the Clipboard</span></span>

<span data-ttu-id="84f03-103"><xref:System.Windows.Forms.Clipboard>類別提供的方法可讓您用來與 Windows 作業系統剪貼簿功能進行互動。</span><span class="sxs-lookup"><span data-stu-id="84f03-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="84f03-104">許多應用程式會使用剪貼簿做為資料的暫存存放庫。</span><span class="sxs-lookup"><span data-stu-id="84f03-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="84f03-105">例如, 字處理器會在剪下和貼上作業期間使用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="84f03-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="84f03-106">剪貼簿也很適合用來將資訊從一個應用程式傳送到另一個。</span><span class="sxs-lookup"><span data-stu-id="84f03-106">The Clipboard is also useful for transferring information from one application to another.</span></span>

<span data-ttu-id="84f03-107">有些應用程式會以多種格式將資料儲存在剪貼簿上, 以增加可能使用資料的其他應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="84f03-107">Some applications store data on the Clipboard in multiple formats to increase the number of other applications that can potentially use the data.</span></span> <span data-ttu-id="84f03-108">剪貼簿格式是可識別格式的字串。</span><span class="sxs-lookup"><span data-stu-id="84f03-108">A Clipboard format is a string that identifies the format.</span></span> <span data-ttu-id="84f03-109">使用已識別格式的應用程式可以抓取剪貼簿上的相關資料。</span><span class="sxs-lookup"><span data-stu-id="84f03-109">An application that uses the identified format can retrieve the associated data on the Clipboard.</span></span> <span data-ttu-id="84f03-110"><xref:System.Windows.Forms.DataFormats>類別會為您的用途提供預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="84f03-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="84f03-111">您也可以使用自己的格式名稱, 或使用物件的類型做為其格式。</span><span class="sxs-lookup"><span data-stu-id="84f03-111">You can also use your own format names or use an object's type as its format.</span></span> <span data-ttu-id="84f03-112">如需將資料新增至剪貼簿的相關[資訊, 請參閱如何:將資料新增至剪貼](how-to-add-data-to-the-clipboard.md)簿。</span><span class="sxs-lookup"><span data-stu-id="84f03-112">For information about adding data to the Clipboard, see [How to: Add Data to the Clipboard](how-to-add-data-to-the-clipboard.md).</span></span>

<span data-ttu-id="84f03-113">若要判斷剪貼簿是否包含特定格式的資料, 請使用其中一`Contains`種*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-113">To determine whether the Clipboard contains data in a particular format, use one of the `Contains`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="84f03-114">若要從剪貼簿取出資料, 請使用其中`Get`一種*格式*方法<xref:System.Windows.Forms.Clipboard.GetData%2A>或方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-114">To retrieve data from the Clipboard, use one of the `Get`*Format* methods or the <xref:System.Windows.Forms.Clipboard.GetData%2A> method.</span></span> <span data-ttu-id="84f03-115">這些方法是 .NET Framework 2.0 中的新功能。</span><span class="sxs-lookup"><span data-stu-id="84f03-115">These methods are new in .NET Framework 2.0.</span></span>

<span data-ttu-id="84f03-116">若要使用早于 .NET Framework 2.0 的版本來存取剪貼簿中的資料<xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> , 請使用方法, 並呼叫所<xref:System.Windows.Forms.IDataObject>傳回之的方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-116">To access data from the Clipboard by using versions earlier than .NET Framework 2.0, use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType> method and call the methods of the returned <xref:System.Windows.Forms.IDataObject>.</span></span> <span data-ttu-id="84f03-117">若要判斷傳回的物件中是否有特定的格式, 例如, 請呼叫<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-117">To determine whether a particular format is available in the returned object, for example, call the <xref:System.Windows.Forms.IDataObject.GetDataPresent%2A> method.</span></span>

> [!NOTE]
> <span data-ttu-id="84f03-118">所有 Windows 應用程式都會共用系統剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="84f03-118">All Windows-based applications share the system Clipboard.</span></span> <span data-ttu-id="84f03-119">因此, 當您切換到另一個應用程式時, 內容可能會變更。</span><span class="sxs-lookup"><span data-stu-id="84f03-119">Therefore, the contents are subject to change when you switch to another application.</span></span>
>
> <span data-ttu-id="84f03-120"><xref:System.Windows.Forms.Clipboard>類別只能用在設定為單一執行緒單元 (STA) 模式的執行緒中。</span><span class="sxs-lookup"><span data-stu-id="84f03-120">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="84f03-121">若要使用這個類別, 請確定`Main`您的方法是<xref:System.STAThreadAttribute>以屬性標記。</span><span class="sxs-lookup"><span data-stu-id="84f03-121">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>

### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="84f03-122">以單一通用格式從剪貼簿取出資料</span><span class="sxs-lookup"><span data-stu-id="84f03-122">To retrieve data from the Clipboard in a single, common format</span></span>

1. <span data-ttu-id="84f03-123"><xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>使用、<xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、或<xref:System.Windows.Forms.Clipboard.GetText%2A>方法。 <xref:System.Windows.Forms.Clipboard.GetImage%2A></span><span class="sxs-lookup"><span data-stu-id="84f03-123">Use the <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>, <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.GetImage%2A>, or <xref:System.Windows.Forms.Clipboard.GetText%2A> method.</span></span> <span data-ttu-id="84f03-124">(選擇性) 先使用`Contains`對應的*格式*方法, 以判斷資料是否以特定格式提供。</span><span class="sxs-lookup"><span data-stu-id="84f03-124">Optionally, use the corresponding `Contains`*Format* methods first to determine whether data is available in a particular format.</span></span> <span data-ttu-id="84f03-125">這些方法僅適用于 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="84f03-125">These methods are available only in .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a><span data-ttu-id="84f03-126">以自訂格式從剪貼簿取出資料</span><span class="sxs-lookup"><span data-stu-id="84f03-126">To retrieve data from the Clipboard in a custom format</span></span>

1. <span data-ttu-id="84f03-127">使用具有<xref:System.Windows.Forms.Clipboard.GetData%2A>自訂格式名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-127">Use the <xref:System.Windows.Forms.Clipboard.GetData%2A> method with a custom format name.</span></span> <span data-ttu-id="84f03-128">這個方法僅適用于 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="84f03-128">This method is available only in .NET Framework 2.0.</span></span>

    <span data-ttu-id="84f03-129">您也可以搭配<xref:System.Windows.Forms.Clipboard.SetData%2A>方法使用預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="84f03-129">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="84f03-130">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。</span><span class="sxs-lookup"><span data-stu-id="84f03-130">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a><span data-ttu-id="84f03-131">以多種格式從剪貼簿取出資料</span><span class="sxs-lookup"><span data-stu-id="84f03-131">To retrieve data from the Clipboard in multiple formats</span></span>

1. <span data-ttu-id="84f03-132">請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="84f03-132">Use the <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> method.</span></span> <span data-ttu-id="84f03-133">您必須使用這個方法, 在早于 .NET Framework 2.0 的版本上, 從剪貼簿取出資料。</span><span class="sxs-lookup"><span data-stu-id="84f03-133">You must use this method to retrieve data from the Clipboard on versions earlier than .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a><span data-ttu-id="84f03-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84f03-134">See also</span></span>

- [<span data-ttu-id="84f03-135">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="84f03-135">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
- [<span data-ttu-id="84f03-136">如何：將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="84f03-136">How to: Add Data to the Clipboard</span></span>](how-to-add-data-to-the-clipboard.md)
