---
title: 作法：巡覽 Windows Forms 中的資料
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964282"
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="b9920-102">HOW TO：巡覽 Windows Forms 中的資料</span><span class="sxs-lookup"><span data-stu-id="b9920-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="b9920-103">在 Windows 應用程式中, 流覽資料來源中之記錄的最簡單方式, 就是將<xref:System.Windows.Forms.BindingSource>元件系結至資料來源, 然後將控制項系<xref:System.Windows.Forms.BindingSource>結至。</span><span class="sxs-lookup"><span data-stu-id="b9920-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="b9920-104">然後<xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, 您可以在這類、 <xref:System.Windows.Forms.BindingSource.MoveLast%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>和<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>上使用內建的導覽方法。</span><span class="sxs-lookup"><span data-stu-id="b9920-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="b9920-105">使用這些方法將會<xref:System.Windows.Forms.BindingSource.Position%2A> <xref:System.Windows.Forms.BindingSource>適當地<xref:System.Windows.Forms.BindingSource.Current%2A>調整的和屬性。</span><span class="sxs-lookup"><span data-stu-id="b9920-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="b9920-106">您也可以藉由設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性來尋找專案, 並將它設定為目前的專案。</span><span class="sxs-lookup"><span data-stu-id="b9920-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="b9920-107">若要遞增資料來源中的位置</span><span class="sxs-lookup"><span data-stu-id="b9920-107">To increment the position in a data source</span></span>  
  
1. <span data-ttu-id="b9920-108">將系結資料的<xref:System.Windows.Forms.BindingSource> 屬性設為要移至的記錄位置。<xref:System.Windows.Forms.BindingSource.Position%2A></span><span class="sxs-lookup"><span data-stu-id="b9920-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="b9920-109">下列<xref:System.Windows.Forms.BindingSource.MoveNext%2A>範例說明<xref:System.Windows.Forms.BindingSource>如何使用的方法, 在按一下時`nextButton`遞增<xref:System.Windows.Forms.BindingSource.Position%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="b9920-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="b9920-110">會與資料集`Northwind`的`Customers`資料表相關聯。 <xref:System.Windows.Forms.BindingSource></span><span class="sxs-lookup"><span data-stu-id="b9920-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9920-111"><xref:System.Windows.Forms.BindingSource.Position%2A>將屬性設定為超過第一個或最後一筆記錄的值並不會產生錯誤, 因為 .NET Framework 不允許您將位置設定為超出清單界限的值。</span><span class="sxs-lookup"><span data-stu-id="b9920-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the .NET Framework will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="b9920-112">如果您的應用程式必須知道您是否已超過第一筆或最後一筆記錄, 請加入邏輯來測試您是否會超出資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="b9920-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="b9920-113">若要檢查您是否已通過結束或開始</span><span class="sxs-lookup"><span data-stu-id="b9920-113">To check whether you have passed the end or beginning</span></span>  
  
1. <span data-ttu-id="b9920-114">建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="b9920-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="b9920-115">在處理常式中, 您可以測試建議的位置值是否已超過實際的資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="b9920-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="b9920-116">下列範例說明如何測試您是否已到達最後一個資料元素。</span><span class="sxs-lookup"><span data-stu-id="b9920-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="b9920-117">在此範例中, 如果您是最後一個元素, 則表單上的 [**下一步]** 按鈕會停用。</span><span class="sxs-lookup"><span data-stu-id="b9920-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b9920-118">請注意, 如果您要變更在程式碼中流覽的清單, 應該重新啟用 [**下一步]** 按鈕, 讓使用者可以流覽新清單的整個長度。</span><span class="sxs-lookup"><span data-stu-id="b9920-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="b9920-119">此外, 請注意<xref:System.Windows.Forms.BindingSource.PositionChanged> , 您所使用之特定<xref:System.Windows.Forms.BindingSource>的事件, 必須與其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="b9920-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="b9920-120">以下是處理<xref:System.Windows.Forms.BindingSource.PositionChanged>事件的方法範例:</span><span class="sxs-lookup"><span data-stu-id="b9920-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="b9920-121">若要尋找專案並將它設定為目前的專案</span><span class="sxs-lookup"><span data-stu-id="b9920-121">To find an item and set it as the current item</span></span>  
  
1. <span data-ttu-id="b9920-122">尋找您想要設定為目前專案的記錄。</span><span class="sxs-lookup"><span data-stu-id="b9920-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="b9920-123">如果您的資料來源已<xref:System.Windows.Forms.BindingSource.Find%2A>完成<xref:System.Windows.Forms.BindingSource>, 您可以使用的方法來執行這項操作。 <xref:System.ComponentModel.IBindingList></span><span class="sxs-lookup"><span data-stu-id="b9920-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="b9920-124">實<xref:System.ComponentModel.IBindingList>作為<xref:System.ComponentModel.BindingList%601>和之資料來源的一些範例。<xref:System.Data.DataView></span><span class="sxs-lookup"><span data-stu-id="b9920-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b9920-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9920-125">See also</span></span>

- [<span data-ttu-id="b9920-126">Windows Forms 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="b9920-126">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)
- [<span data-ttu-id="b9920-127">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="b9920-127">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="b9920-128">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b9920-128">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
- [<span data-ttu-id="b9920-129">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="b9920-129">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
