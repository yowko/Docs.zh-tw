---
title: HOW TO：實作屬性變更通知
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: d37d468acc94470be8c2afdc495b40168932ec83
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931439"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="9cd2b-102">HOW TO：實作屬性變更通知</span><span class="sxs-lookup"><span data-stu-id="9cd2b-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="9cd2b-103">若要支援<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>繫結而讓您能自動反映繫結來源 （例如，將會自動更新，當使用者編輯表單的 [預覽] 窗格），動態變更的繫結目標屬性類別必須提供適當的屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="9cd2b-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="9cd2b-104">此範例示範如何建立可實作類別<xref:System.ComponentModel.INotifyPropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="9cd2b-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd2b-105">範例</span><span class="sxs-lookup"><span data-stu-id="9cd2b-105">Example</span></span>  
 <span data-ttu-id="9cd2b-106">若要實作<xref:System.ComponentModel.INotifyPropertyChanged>您需要宣告<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件，並建立`OnPropertyChanged`方法。</span><span class="sxs-lookup"><span data-stu-id="9cd2b-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="9cd2b-107">然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="9cd2b-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="9cd2b-108">若要查看範例如何`Person`類別可以用來支援<xref:System.Windows.Data.BindingMode.TwoWay>繫結，請參閱[控制 TextBox 文字更新來源的時機](how-to-control-when-the-textbox-text-updates-the-source.md)。</span><span class="sxs-lookup"><span data-stu-id="9cd2b-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cd2b-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cd2b-109">See also</span></span>

- [<span data-ttu-id="9cd2b-110">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="9cd2b-110">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="9cd2b-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="9cd2b-111">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="9cd2b-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="9cd2b-112">How-to Topics</span></span>](data-binding-how-to-topics.md)
