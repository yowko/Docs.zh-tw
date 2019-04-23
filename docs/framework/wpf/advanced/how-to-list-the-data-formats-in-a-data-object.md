---
title: HOW TO：列出資料物件中的資料格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drag-and-drop [WPF], listing data formats
- DataFormats class [WPF]
- data formats [WPF], listing
ms.assetid: 18e7ba4b-ccef-4815-ae2d-3a32891010c0
ms.openlocfilehash: f8230eac33a18a0d99cc757d54c2b901c1afe977
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077741"
---
# <a name="how-to-list-the-data-formats-in-a-data-object"></a><span data-ttu-id="27aab-102">HOW TO：列出資料物件中的資料格式</span><span class="sxs-lookup"><span data-stu-id="27aab-102">How to: List the Data Formats in a Data Object</span></span>
<span data-ttu-id="27aab-103">下列範例示範如何使用<xref:System.Windows.DataObject.GetFormats%2A>方法多載取得用以表示使用資料物件中每個資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="27aab-103">The following examples show how to use the <xref:System.Windows.DataObject.GetFormats%2A> method overloads get an array of strings denoting each data format that is available in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="27aab-104">範例</span><span class="sxs-lookup"><span data-stu-id="27aab-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27aab-105">描述</span><span class="sxs-lookup"><span data-stu-id="27aab-105">Description</span></span>  
 <span data-ttu-id="27aab-106">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示資料物件 （原生和自動轉換） 中可用的所有資料格式的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="27aab-106">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting all data formats available in a data object (both native and auto-convertible).</span></span>  
  
### <a name="code"></a><span data-ttu-id="27aab-107">程式碼</span><span class="sxs-lookup"><span data-stu-id="27aab-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats)]  
  
## <a name="example"></a><span data-ttu-id="27aab-108">範例</span><span class="sxs-lookup"><span data-stu-id="27aab-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="27aab-109">描述</span><span class="sxs-lookup"><span data-stu-id="27aab-109">Description</span></span>  
 <span data-ttu-id="27aab-110">下列範例程式碼使用<xref:System.Windows.DataObject.GetFormats%2A>多載，以取得用來表示只有可用的資料格式的資料物件 （自動轉換的資料格式會進行篩選） 中的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="27aab-110">The following example code uses the <xref:System.Windows.DataObject.GetFormats%2A> overload to get an array of strings denoting only data formats available in a data object (auto-convertible data formats are filtered).</span></span>  
  
### <a name="code"></a><span data-ttu-id="27aab-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="27aab-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_getalldataformats_nativeonly)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_GetAllDataFormats_NativeOnly](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_getalldataformats_nativeonly)]  
  
## <a name="see-also"></a><span data-ttu-id="27aab-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27aab-112">See also</span></span>

- <xref:System.Windows.IDataObject>
- [<span data-ttu-id="27aab-113">拖放概觀</span><span class="sxs-lookup"><span data-stu-id="27aab-113">Drag and Drop Overview</span></span>](drag-and-drop-overview.md)
