---
title: 如何：流覽資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 2dd900b652b0ff21ea0eb0dbc5463b22c869ec7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739395"
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="13028-102">如何：巡覽 Windows Form 中的資料</span><span class="sxs-lookup"><span data-stu-id="13028-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="13028-103">在 Windows 應用程式中，流覽資料來源中之記錄的最簡單方式，就是將 <xref:System.Windows.Forms.BindingSource> 元件系結至資料來源，然後將控制項系結至 <xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="13028-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="13028-104">然後，您可以在 <xref:System.Windows.Forms.BindingSource> 上使用內建的導覽方法，例如 <xref:System.Windows.Forms.BindingSource.MoveNext%2A>、<xref:System.Windows.Forms.BindingSource.MoveLast%2A>、<xref:System.Windows.Forms.BindingSource.MovePrevious%2A> 和 <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>。</span><span class="sxs-lookup"><span data-stu-id="13028-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="13028-105">使用這些方法將會適當地調整 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.Position%2A> 和 <xref:System.Windows.Forms.BindingSource.Current%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13028-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="13028-106">您也可以藉由設定 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性來尋找專案，並將它設定為目前的專案。</span><span class="sxs-lookup"><span data-stu-id="13028-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="13028-107">若要遞增資料來源中的位置</span><span class="sxs-lookup"><span data-stu-id="13028-107">To increment the position in a data source</span></span>  
  
1. <span data-ttu-id="13028-108">將系結資料之 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性，設定為要移至的記錄位置。</span><span class="sxs-lookup"><span data-stu-id="13028-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="13028-109">下列範例說明如何使用 <xref:System.Windows.Forms.BindingSource> 的 <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 方法，在按一下 `nextButton` 時遞增 <xref:System.Windows.Forms.BindingSource.Position%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="13028-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="13028-110"><xref:System.Windows.Forms.BindingSource> 與資料集 `Northwind`的 `Customers` 資料表相關聯。</span><span class="sxs-lookup"><span data-stu-id="13028-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="13028-111">將 [<xref:System.Windows.Forms.BindingSource.Position%2A>] 屬性設為超過第一個或最後一筆記錄的值並不會產生錯誤，因為 .NET Framework 不允許您將位置設定為超出清單界限的值。</span><span class="sxs-lookup"><span data-stu-id="13028-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the .NET Framework will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="13028-112">如果您的應用程式必須知道您是否已超過第一筆或最後一筆記錄，請加入邏輯來測試您是否會超出資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="13028-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="13028-113">若要檢查您是否已通過結束或開始</span><span class="sxs-lookup"><span data-stu-id="13028-113">To check whether you have passed the end or beginning</span></span>  
  
1. <span data-ttu-id="13028-114">建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="13028-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="13028-115">在處理常式中，您可以測試建議的位置值是否已超過實際的資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="13028-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="13028-116">下列範例說明如何測試您是否已到達最後一個資料元素。</span><span class="sxs-lookup"><span data-stu-id="13028-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="13028-117">在此範例中，如果您是最後一個元素，則表單上的 [**下一步]** 按鈕會停用。</span><span class="sxs-lookup"><span data-stu-id="13028-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="13028-118">請注意，如果您要變更在程式碼中流覽的清單，應該重新啟用 [**下一步]** 按鈕，讓使用者可以流覽新清單的整個長度。</span><span class="sxs-lookup"><span data-stu-id="13028-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="13028-119">此外，請注意，您所使用之特定 <xref:System.Windows.Forms.BindingSource> 的上述 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件，必須與其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="13028-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="13028-120">以下是處理 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的方法範例：</span><span class="sxs-lookup"><span data-stu-id="13028-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="13028-121">若要尋找專案並將它設定為目前的專案</span><span class="sxs-lookup"><span data-stu-id="13028-121">To find an item and set it as the current item</span></span>  
  
1. <span data-ttu-id="13028-122">尋找您想要設定為目前專案的記錄。</span><span class="sxs-lookup"><span data-stu-id="13028-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="13028-123">如果您的資料來源會進行 <xref:System.ComponentModel.IBindingList>，您可以使用 <xref:System.Windows.Forms.BindingSource>的 <xref:System.Windows.Forms.BindingSource.Find%2A> 方法來執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="13028-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="13028-124">一些執行 <xref:System.ComponentModel.IBindingList> 的資料來源範例 <xref:System.ComponentModel.BindingList%601> 和 <xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="13028-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="13028-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13028-125">See also</span></span>

- [<span data-ttu-id="13028-126">Windows Forms 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="13028-126">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)
- [<span data-ttu-id="13028-127">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="13028-127">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="13028-128">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13028-128">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
- [<span data-ttu-id="13028-129">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="13028-129">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
