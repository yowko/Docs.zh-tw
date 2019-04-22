---
title: HOW TO：將多種資料格式儲存在資料物件中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], storing multiple formats
- DataFormats class [WPF], storing multiple formats
- drag-and-drop [WPF], storing multiple formats
ms.assetid: 941ace29-29c4-4c26-b75b-ea7d06aa0d69
ms.openlocfilehash: 3f8e7233e1d28fec1f7dac114b04287aa3aff49f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59085047"
---
# <a name="how-to-store-multiple-data-formats-in-a-data-object"></a><span data-ttu-id="cee24-102">HOW TO：將多種資料格式儲存在資料物件中</span><span class="sxs-lookup"><span data-stu-id="cee24-102">How to: Store Multiple Data Formats in a Data Object</span></span>
<span data-ttu-id="cee24-103">下列範例示範如何使用<xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29>方法，以將資料加入至多個格式中的資料物件。</span><span class="sxs-lookup"><span data-stu-id="cee24-103">The following example shows how to use the <xref:System.Windows.DataObject.SetData%28System.String%2CSystem.Object%29> method to add data to a data object in multiple formats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cee24-104">範例</span><span class="sxs-lookup"><span data-stu-id="cee24-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cee24-105">描述</span><span class="sxs-lookup"><span data-stu-id="cee24-105">Description</span></span>  
  
### <a name="code"></a><span data-ttu-id="cee24-106">程式碼</span><span class="sxs-lookup"><span data-stu-id="cee24-106">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_storemultipleformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_StoreMultipleFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_storemultipleformats)]  
  
## <a name="see-also"></a><span data-ttu-id="cee24-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cee24-107">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="cee24-108">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="cee24-108">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
