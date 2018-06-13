---
title: 如何：巡覽 Windows Form 中的資料
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
ms.openlocfilehash: 9572c1234c07c77d5df0c9cd58499faafe460e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540364"
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="6dd93-102">如何：巡覽 Windows Form 中的資料</span><span class="sxs-lookup"><span data-stu-id="6dd93-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="6dd93-103">在 Windows 應用程式中，瀏覽資料來源中的記錄最簡單方式是將繫結<xref:System.Windows.Forms.BindingSource>元件至資料來源，然後將控制項繫結至<xref:System.Windows.Forms.BindingSource>。</span><span class="sxs-lookup"><span data-stu-id="6dd93-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="6dd93-104">然後您可以使用內建瀏覽方法上<xref:System.Windows.Forms.BindingSource>這類<xref:System.Windows.Forms.BindingSource.MoveNext%2A>， <xref:System.Windows.Forms.BindingSource.MoveLast%2A>，<xref:System.Windows.Forms.BindingSource.MovePrevious%2A>和<xref:System.Windows.Forms.BindingSource.MoveFirst%2A>。</span><span class="sxs-lookup"><span data-stu-id="6dd93-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="6dd93-105">使用這些方法將會調整<xref:System.Windows.Forms.BindingSource.Position%2A>和<xref:System.Windows.Forms.BindingSource.Current%2A>屬性<xref:System.Windows.Forms.BindingSource>適當。</span><span class="sxs-lookup"><span data-stu-id="6dd93-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="6dd93-106">您也可以尋找項目，並將它設為目前的項目中，藉由設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="6dd93-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="6dd93-107">要遞增的資料來源中的位置</span><span class="sxs-lookup"><span data-stu-id="6dd93-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="6dd93-108">設定<xref:System.Windows.Forms.BindingSource.Position%2A>屬性<xref:System.Windows.Forms.BindingSource>繫結至資料錄位置移至資料。</span><span class="sxs-lookup"><span data-stu-id="6dd93-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="6dd93-109">下列範例說明如何使用<xref:System.Windows.Forms.BindingSource.MoveNext%2A>方法<xref:System.Windows.Forms.BindingSource>遞增<xref:System.Windows.Forms.BindingSource.Position%2A>屬性時`nextButton`按下。</span><span class="sxs-lookup"><span data-stu-id="6dd93-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="6dd93-110"><xref:System.Windows.Forms.BindingSource>聯`Customers`資料表的資料集`Northwind`。</span><span class="sxs-lookup"><span data-stu-id="6dd93-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6dd93-111">設定<xref:System.Windows.Forms.BindingSource.Position%2A>超過第一個或最後一個記錄的值的屬性不會導致發生錯誤時，為[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]將不允許您將位置設定的值超出清單的範圍。</span><span class="sxs-lookup"><span data-stu-id="6dd93-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="6dd93-112">如果您的應用程式知道您是否超過第一個或最後一筆資料錄中重要，，包括邏輯，以測試是否會超過資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="6dd93-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="6dd93-113">若要檢查是否超過結尾或開頭</span><span class="sxs-lookup"><span data-stu-id="6dd93-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="6dd93-114">建立 <xref:System.Windows.Forms.BindingSource.PositionChanged> 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6dd93-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="6dd93-115">在處理常式中，您可以測試是否建議的位置值已超過實際的資料元素計數。</span><span class="sxs-lookup"><span data-stu-id="6dd93-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="6dd93-116">下列範例說明如何測試是否已達到最後一個資料元素。</span><span class="sxs-lookup"><span data-stu-id="6dd93-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="6dd93-117">在範例中，如果您在最後一個項目，**下一步**表單上的按鈕已停用。</span><span class="sxs-lookup"><span data-stu-id="6dd93-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6dd93-118">請注意，您應該變更程式碼中巡覽的清單，您應該重新啟用**下一步**按鈕，使用者可能瀏覽整個新清單的長度。</span><span class="sxs-lookup"><span data-stu-id="6dd93-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="6dd93-119">此外，請注意，上述<xref:System.Windows.Forms.BindingSource.PositionChanged>特定事件<xref:System.Windows.Forms.BindingSource>您正在使用必須為其事件處理方法相關聯。</span><span class="sxs-lookup"><span data-stu-id="6dd93-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="6dd93-120">下列是一種方法處理的範例<xref:System.Windows.Forms.BindingSource.PositionChanged>事件：</span><span class="sxs-lookup"><span data-stu-id="6dd93-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="6dd93-121">尋找項目，並將它設為目前的項目</span><span class="sxs-lookup"><span data-stu-id="6dd93-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="6dd93-122">尋找您想要設定為目前的項目記錄。</span><span class="sxs-lookup"><span data-stu-id="6dd93-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="6dd93-123">您可以使用<xref:System.Windows.Forms.BindingSource.Find%2A>方法<xref:System.Windows.Forms.BindingSource>，如果您的資料來源實作<xref:System.ComponentModel.IBindingList>。</span><span class="sxs-lookup"><span data-stu-id="6dd93-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="6dd93-124">一些範例資料的來源可實作<xref:System.ComponentModel.IBindingList>是<xref:System.ComponentModel.BindingList%601>和<xref:System.Data.DataView>。</span><span class="sxs-lookup"><span data-stu-id="6dd93-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6dd93-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dd93-125">See Also</span></span>  
 [<span data-ttu-id="6dd93-126">Windows Forms 支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="6dd93-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="6dd93-127">Windows Forms 資料繫結中的變更告知</span><span class="sxs-lookup"><span data-stu-id="6dd93-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="6dd93-128">資料繫結和 Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6dd93-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="6dd93-129">Windows Forms 資料繫結</span><span class="sxs-lookup"><span data-stu-id="6dd93-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
