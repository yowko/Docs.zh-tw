---
title: 操作說明：實作屬性變更通知
description: 當屬性值在 Windows Presentation Foundation （WPF）中變更時，讓您的屬性自動通知系結來源。
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620777"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="0ea35-103">操作說明：實作屬性變更通知</span><span class="sxs-lookup"><span data-stu-id="0ea35-103">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="0ea35-104">若要支援或系結，讓您的系結 <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> 目標屬性自動反映系結來源的動態變更（例如，當使用者編輯表單時，自動更新預覽窗格），您的類別必須提供適當的屬性變更通知。</span><span class="sxs-lookup"><span data-stu-id="0ea35-104">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="0ea35-105">這個範例會示範如何建立可執行檔類別 <xref:System.ComponentModel.INotifyPropertyChanged> 。</span><span class="sxs-lookup"><span data-stu-id="0ea35-105">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ea35-106">範例</span><span class="sxs-lookup"><span data-stu-id="0ea35-106">Example</span></span>  
 <span data-ttu-id="0ea35-107">若要執行， <xref:System.ComponentModel.INotifyPropertyChanged> 您需要宣告 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> 事件並建立 `OnPropertyChanged` 方法。</span><span class="sxs-lookup"><span data-stu-id="0ea35-107">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="0ea35-108">然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="0ea35-108">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="0ea35-109">若要查看如何 `Person` 使用類別來支援系結的範例 <xref:System.Windows.Data.BindingMode.TwoWay> ，請參閱[控制 TextBox 文字更新來源](how-to-control-when-the-textbox-text-updates-the-source.md)的時機。</span><span class="sxs-lookup"><span data-stu-id="0ea35-109">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ea35-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ea35-110">See also</span></span>

- [<span data-ttu-id="0ea35-111">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="0ea35-111">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="0ea35-112">資料系結總覽</span><span class="sxs-lookup"><span data-stu-id="0ea35-112">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="0ea35-113">操作說明主題</span><span class="sxs-lookup"><span data-stu-id="0ea35-113">How-to Topics</span></span>](data-binding-how-to-topics.md)
