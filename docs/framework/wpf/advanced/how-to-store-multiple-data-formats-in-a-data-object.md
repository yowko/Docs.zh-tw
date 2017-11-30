---
title: "如何：將多個資料格式儲存在資料物件中"
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
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b7019385e9c6acd8baf74dac163b75b10307a7f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="a4dcb-102">如何：將多個資料格式儲存在資料物件中</span><span class="sxs-lookup"><span data-stu-id="a4dcb-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="a4dcb-103">下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。</span><span class="sxs-lookup"><span data-stu-id="a4dcb-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4dcb-104">範例</span><span class="sxs-lookup"><span data-stu-id="a4dcb-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a4dcb-105">描述</span><span class="sxs-lookup"><span data-stu-id="a4dcb-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="a4dcb-106">程式碼</span><span class="sxs-lookup"><span data-stu-id="a4dcb-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="a4dcb-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4dcb-107">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="a4dcb-108">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="a4dcb-108">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
