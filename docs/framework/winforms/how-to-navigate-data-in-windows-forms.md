---
title: HOW TO：巡覽 Windows Forms 中的資料
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
ms.openlocfilehash: 2ba33f9ecb3a12a62c41af17d3f9ad6f6e3f8a5d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344997"
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="bcbd1-102">HOW TO：巡覽 Windows Forms 中的資料</span><span class="sxs-lookup"><span data-stu-id="bcbd1-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="bcbd1-103">在 Windows 應用程式中，瀏覽資料來源中記錄的最簡單方式是繫結<xref:System.Windows.Forms.BindingSource>元件至資料來源，然後將控制項繫結至<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="bcbd1-104">然後您可以使用內建的巡覽方法上<xref:System.Windows.Forms.BindingSource>這類<xref:System.Windows.Forms.BindingSource.MoveNext%2A>， <xref:System.Windows.Forms.BindingSource.MoveLast%2A>，<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>和<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="bcbd1-105">使用這些方法會自動調整<xref:System.Windows.Forms.BindingSource.Position%2A>並<xref:System.Windows.Forms.BindingSource.Current%2A>屬性的<xref:System.Windows.Forms.BindingSource>適當。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="bcbd1-106">您也可以尋找項目，並將它設為目前的項目中，藉由設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="bcbd1-107">要遞增的資料來源中的位置</span><span class="sxs-lookup"><span data-stu-id="bcbd1-107">To increment the position in a data source</span></span>  
  
1. <span data-ttu-id="bcbd1-108">設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性<xref:System.Windows.Forms.BindingSource>繫結資料移至的記錄位置。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="bcbd1-109">下列範例說明如何利用<xref:System.Windows.Forms.BindingSource.MoveNext%2A>方法<xref:System.Windows.Forms.BindingSource>遞增<xref:System.Windows.Forms.BindingSource.Position%2A>屬性時`nextButton`按下。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="bcbd1-110"><xref:System.Windows.Forms.BindingSource>相關聯`Customers`資料表的資料集`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bcbd1-111">設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性設為值之外的第一個或最後一筆記錄不會導致發生錯誤時，為[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]將不允許您將位置設定的值超出清單的範圍。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="bcbd1-112">如果您知道是否您已經看過的第一個或最後一筆記錄的應用程式中很重要，，包括邏輯，以測試是否就會超出資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="bcbd1-113">若要檢查是否已通過結尾或開頭</span><span class="sxs-lookup"><span data-stu-id="bcbd1-113">To check whether you have passed the end or beginning</span></span>  
  
1. <span data-ttu-id="bcbd1-114">建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="bcbd1-115">在處理常式中，您可以測試是否建議的位置值已超過實際的資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="bcbd1-116">下列範例說明如何測試是否已到達最後一個資料元素。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="bcbd1-117">在範例中，如果您在最後一個元素，**下一步**表單上的按鈕已停用。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bcbd1-118">請注意，您應該變更您瀏覽程式碼中的清單，您應該重新啟用**下一步**按鈕，以便使用者可以瀏覽新的清單中的整個長度。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="bcbd1-119">此外，請注意，上述<xref:System.Windows.Forms.BindingSource.PositionChanged>特定的事件<xref:System.Windows.Forms.BindingSource>您正在使用必須為其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="bcbd1-120">以下是針對處理方法的範例<xref:System.Windows.Forms.BindingSource.PositionChanged>事件：</span><span class="sxs-lookup"><span data-stu-id="bcbd1-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="bcbd1-121">尋找項目，並將它設為目前的項目</span><span class="sxs-lookup"><span data-stu-id="bcbd1-121">To find an item and set it as the current item</span></span>  
  
1. <span data-ttu-id="bcbd1-122">尋找您想要設定為目前的項目記錄。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="bcbd1-123">您可以使用<xref:System.Windows.Forms.BindingSource.Find%2A>方法<xref:System.Windows.Forms.BindingSource>，如果您的資料來源實作<xref:System.ComponentModel.IBindingList>。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="bcbd1-124">資料的一些範例來源可實<xref:System.ComponentModel.IBindingList>都<xref:System.ComponentModel.BindingList%601>和<xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="bcbd1-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bcbd1-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcbd1-125">See also</span></span>

- [<span data-ttu-id="bcbd1-126">Windows Form 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="bcbd1-126">Data Sources Supported by Windows Forms</span></span>](data-sources-supported-by-windows-forms.md)
- [<span data-ttu-id="bcbd1-127">Windows Form 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="bcbd1-127">Change Notification in Windows Forms Data Binding</span></span>](change-notification-in-windows-forms-data-binding.md)
- [<span data-ttu-id="bcbd1-128">資料繫結和 Windows Form</span><span class="sxs-lookup"><span data-stu-id="bcbd1-128">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
- [<span data-ttu-id="bcbd1-129">Windows Form 資料繫結</span><span class="sxs-lookup"><span data-stu-id="bcbd1-129">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
