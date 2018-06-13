---
title: 如何：判斷資料格式是否出現在資料物件中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: e3e2f47df0ae1fdf0fe875827473f2c3a1b53fb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543415"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="c3511-102">如何：判斷資料格式是否出現在資料物件中</span><span class="sxs-lookup"><span data-stu-id="c3511-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="c3511-103">下列範例示範如何使用各種<xref:System.Windows.DataObject.GetDataPresent%2A>方法是否出現在 資料物件中特定的資料格式多載來查詢。</span><span class="sxs-lookup"><span data-stu-id="c3511-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3511-104">範例</span><span class="sxs-lookup"><span data-stu-id="c3511-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c3511-105">描述</span><span class="sxs-lookup"><span data-stu-id="c3511-105">Description</span></span>  
 <span data-ttu-id="c3511-106">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載，以便查詢是否有特定的資料格式的描述項字串。</span><span class="sxs-lookup"><span data-stu-id="c3511-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3511-107">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3511-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="c3511-108">範例</span><span class="sxs-lookup"><span data-stu-id="c3511-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c3511-109">描述</span><span class="sxs-lookup"><span data-stu-id="c3511-109">Description</span></span>  
 <span data-ttu-id="c3511-110">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.Type%29>多載來查詢特定的資料格式的類型是否存在。</span><span class="sxs-lookup"><span data-stu-id="c3511-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3511-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3511-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="c3511-112">範例</span><span class="sxs-lookup"><span data-stu-id="c3511-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c3511-113">描述</span><span class="sxs-lookup"><span data-stu-id="c3511-113">Description</span></span>  
 <span data-ttu-id="c3511-114">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>依描述項字串多載來查詢資料，並指定如何處理自動轉換的資料格式。</span><span class="sxs-lookup"><span data-stu-id="c3511-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3511-115">程式碼</span><span class="sxs-lookup"><span data-stu-id="c3511-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="c3511-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3511-116">See Also</span></span>  
 <xref:System.Windows.IDataObject>
