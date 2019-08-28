---
title: HOW TO：將資料新增至剪貼簿
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 0d9b82f01080d18353ecb91578a8005260bbe739
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044226"
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="52b26-102">作法：將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="52b26-102">How to: Add Data to the Clipboard</span></span>

<span data-ttu-id="52b26-103"><xref:System.Windows.Forms.Clipboard>類別提供的方法可讓您用來與 Windows 作業系統剪貼簿功能進行互動。</span><span class="sxs-lookup"><span data-stu-id="52b26-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="52b26-104">許多應用程式會使用剪貼簿做為資料的暫存存放庫。</span><span class="sxs-lookup"><span data-stu-id="52b26-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="52b26-105">例如, 字處理器會在剪下和貼上作業期間使用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="52b26-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="52b26-106">剪貼簿也適用于將資料從一個應用程式傳送到另一個。</span><span class="sxs-lookup"><span data-stu-id="52b26-106">The Clipboard is also useful for transferring data from one application to another.</span></span>

<span data-ttu-id="52b26-107">當您將資料新增至剪貼簿時, 您可以指定資料格式, 讓其他應用程式可以使用該格式來辨識資料。</span><span class="sxs-lookup"><span data-stu-id="52b26-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="52b26-108">您也可以使用多種不同的格式將資料新增至剪貼簿, 以增加可能使用該資料的其他應用程式數目。</span><span class="sxs-lookup"><span data-stu-id="52b26-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>

<span data-ttu-id="52b26-109">剪貼簿格式是識別格式的字串, 因此使用該格式的應用程式可以抓取相關聯的資料。</span><span class="sxs-lookup"><span data-stu-id="52b26-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="52b26-110"><xref:System.Windows.Forms.DataFormats>類別會為您的用途提供預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="52b26-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="52b26-111">您也可以使用自己的格式名稱, 或使用物件的類型做為其格式。</span><span class="sxs-lookup"><span data-stu-id="52b26-111">You can also use your own format names or use the type of an object as its format.</span></span>

<span data-ttu-id="52b26-112">若要以一或多個格式將資料新增至剪貼簿<xref:System.Windows.Forms.Clipboard.SetDataObject%2A> , 請使用方法。</span><span class="sxs-lookup"><span data-stu-id="52b26-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="52b26-113">您可以將任何物件傳遞至此方法, 但是若要以多種格式加入資料, 您必須先將資料新增至專為使用多種格式而設計的個別物件。</span><span class="sxs-lookup"><span data-stu-id="52b26-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="52b26-114">一般來說, 您會將資料加入至<xref:System.Windows.Forms.DataObject>, 但是您可以使用任何可實作為<xref:System.Windows.Forms.IDataObject>介面的型別。</span><span class="sxs-lookup"><span data-stu-id="52b26-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>

<span data-ttu-id="52b26-115">在 .NET Framework 2.0 中, 您可以使用新的方法, 將資料直接加入剪貼簿, 使基本剪貼簿工作更容易。</span><span class="sxs-lookup"><span data-stu-id="52b26-115">In .NET Framework 2.0, you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="52b26-116">當您以單一通用格式 (例如文字) 處理資料時, 請使用這些方法。</span><span class="sxs-lookup"><span data-stu-id="52b26-116">Use these methods when you work with data in a single, common format such as text.</span></span>

> [!NOTE]
> <span data-ttu-id="52b26-117">所有 Windows 應用程式都會共用剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="52b26-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="52b26-118">因此, 當您切換到另一個應用程式時, 內容可能會變更。</span><span class="sxs-lookup"><span data-stu-id="52b26-118">Therefore, the contents are subject to change when you switch to another application.</span></span>
>
> <span data-ttu-id="52b26-119"><xref:System.Windows.Forms.Clipboard>類別只能用在設定為單一執行緒單元 (STA) 模式的執行緒中。</span><span class="sxs-lookup"><span data-stu-id="52b26-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="52b26-120">若要使用這個類別, 請確定`Main`您的方法是<xref:System.STAThreadAttribute>以屬性標記。</span><span class="sxs-lookup"><span data-stu-id="52b26-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>
>
> <span data-ttu-id="52b26-121">物件必須是可序列化的, 才能放在剪貼簿上。</span><span class="sxs-lookup"><span data-stu-id="52b26-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="52b26-122">若要讓類型成為可序列化, 請將<xref:System.SerializableAttribute>它標記為屬性。</span><span class="sxs-lookup"><span data-stu-id="52b26-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="52b26-123">如果您將不可序列化的物件傳遞至剪貼簿方法, 此方法將會失敗, 而不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="52b26-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="52b26-124">如需序列化的詳細資訊，請參閱 <xref:System.Runtime.Serialization>。</span><span class="sxs-lookup"><span data-stu-id="52b26-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>

### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="52b26-125">以單一通用格式將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="52b26-125">To add data to the Clipboard in a single, common format</span></span>

1. <span data-ttu-id="52b26-126"><xref:System.Windows.Forms.Clipboard.SetAudio%2A>使用、<xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。 <xref:System.Windows.Forms.Clipboard.SetImage%2A></span><span class="sxs-lookup"><span data-stu-id="52b26-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="52b26-127">這些方法僅適用于 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="52b26-127">These methods are available only in .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
    [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]

### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="52b26-128">以自訂格式將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="52b26-128">To add data to the Clipboard in a custom format</span></span>

1. <span data-ttu-id="52b26-129">使用具有<xref:System.Windows.Forms.Clipboard.SetData%2A>自訂格式名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="52b26-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="52b26-130">這個方法僅適用于 .NET Framework 2.0。</span><span class="sxs-lookup"><span data-stu-id="52b26-130">This method is available only in .NET Framework 2.0.</span></span>

    <span data-ttu-id="52b26-131">您也可以搭配<xref:System.Windows.Forms.Clipboard.SetData%2A>方法使用預先定義的格式名稱。</span><span class="sxs-lookup"><span data-stu-id="52b26-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="52b26-132">如需詳細資訊，請參閱 <xref:System.Windows.Forms.DataFormats>。</span><span class="sxs-lookup"><span data-stu-id="52b26-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
    [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="52b26-133">以多種格式將資料新增至剪貼簿</span><span class="sxs-lookup"><span data-stu-id="52b26-133">To add data to the Clipboard in multiple formats</span></span>

1. <span data-ttu-id="52b26-134">使用方法, 並傳入<xref:System.Windows.Forms.DataObject>包含您資料的。 <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="52b26-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="52b26-135">您必須使用這個方法, 在 .NET Framework 2.0 之前的版本上, 將資料新增至剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="52b26-135">You must use this method to add data to the Clipboard on versions earlier than .NET Framework 2.0.</span></span>

    [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
    [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]

## <a name="see-also"></a><span data-ttu-id="52b26-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52b26-136">See also</span></span>

- [<span data-ttu-id="52b26-137">拖放作業和剪貼簿支援</span><span class="sxs-lookup"><span data-stu-id="52b26-137">Drag-and-Drop Operations and Clipboard Support</span></span>](drag-and-drop-operations-and-clipboard-support.md)
- [<span data-ttu-id="52b26-138">如何：從剪貼簿取出資料</span><span class="sxs-lookup"><span data-stu-id="52b26-138">How to: Retrieve Data from the Clipboard</span></span>](how-to-retrieve-data-from-the-clipboard.md)
