---
title: "操作說明：實作屬性變更通知"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6628ec27ab381f52a086cac3f8d0cd92aea2cd8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="75630-102">操作說明：實作屬性變更通知</span><span class="sxs-lookup"><span data-stu-id="75630-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="75630-103">若要支援<xref:System.Windows.Data.BindingMode.OneWay>或<xref:System.Windows.Data.BindingMode.TwoWay>繫結至啟用您的繫結目標屬性，以自動反映繫結來源 （例如，讓使用者編輯表單時，自動更新 [預覽] 窗格），動態變更您的類別必須提供適當的屬性已變更通知。</span><span class="sxs-lookup"><span data-stu-id="75630-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="75630-104">這個範例示範如何建立類別，實作<xref:System.ComponentModel.INotifyPropertyChanged>。</span><span class="sxs-lookup"><span data-stu-id="75630-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75630-105">範例</span><span class="sxs-lookup"><span data-stu-id="75630-105">Example</span></span>  
 <span data-ttu-id="75630-106">若要實作<xref:System.ComponentModel.INotifyPropertyChanged>您需要宣告<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>事件，並建立`OnPropertyChanged`方法。</span><span class="sxs-lookup"><span data-stu-id="75630-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="75630-107">然後，對於您想變更通知的每個屬性，您會在每回更新屬性時呼叫 `OnPropertyChanged`。</span><span class="sxs-lookup"><span data-stu-id="75630-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="75630-108">若要查看如何的範例`Person`類別可以用來支援<xref:System.Windows.Data.BindingMode.TwoWay>繫結，請參閱[控制當文字方塊的文字更新來源](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)。</span><span class="sxs-lookup"><span data-stu-id="75630-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75630-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="75630-109">See Also</span></span>  
 [<span data-ttu-id="75630-110">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="75630-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="75630-111">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="75630-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="75630-112">HOW-TO 主題</span><span class="sxs-lookup"><span data-stu-id="75630-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
