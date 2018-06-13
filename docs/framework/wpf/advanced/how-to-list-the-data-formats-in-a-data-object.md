---
title: 如何：列出資料物件中的資料格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: c0e5917d52d9253737a56307beed69bc0255807c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543477"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="0dbfd-102">如何：列出資料物件中的資料格式</span><span class="sxs-lookup"><span data-stu-id="0dbfd-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="0dbfd-103">下列範例顯示如何使用<xref:System.Windows.DataObject.GetFormats%2A>方法多載取得此項表示應使用資料物件中每一種資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0dbfd-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dbfd-104">範例</span><span class="sxs-lookup"><span data-stu-id="0dbfd-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0dbfd-105">描述</span><span class="sxs-lookup"><span data-stu-id="0dbfd-105">Description</span></span>  
 <span data-ttu-id="0dbfd-106">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載來取得代表可用資料物件 （原生和自動轉換） 中的所有資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0dbfd-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="0dbfd-107">程式碼</span><span class="sxs-lookup"><span data-stu-id="0dbfd-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="0dbfd-108">範例</span><span class="sxs-lookup"><span data-stu-id="0dbfd-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0dbfd-109">描述</span><span class="sxs-lookup"><span data-stu-id="0dbfd-109">Description</span></span>  
 <span data-ttu-id="0dbfd-110">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得此項表示應只可用的資料格式的資料物件 （自動轉換的資料格式會篩選） 中的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0dbfd-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="0dbfd-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="0dbfd-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="0dbfd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dbfd-112">See Also</span></span>  
 <xref:System.Windows.IDataObject>  
 [<span data-ttu-id="0dbfd-113">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="0dbfd-113">Drag and Drop Overview</span></span>](../../../../docs/framework/wpf/advanced/drag-and-drop-overview.md)
