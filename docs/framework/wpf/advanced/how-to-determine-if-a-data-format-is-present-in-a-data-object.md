---
title: HOW TO：判斷資料物件中是否有資料格式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 4cec733490e2a9dc5d54b3b253ac38a5090ac885
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768744"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a><span data-ttu-id="cab10-102">HOW TO：判斷資料物件中是否有資料格式</span><span class="sxs-lookup"><span data-stu-id="cab10-102">How to: Determine if a Data Format is Present in a Data Object</span></span>
<span data-ttu-id="cab10-103">下列範例示範如何使用各種<xref:System.Windows.DataObject.GetDataPresent%2A>方法進行多載以查詢特定資料格式是否出現在資料物件。</span><span class="sxs-lookup"><span data-stu-id="cab10-103">The following examples show how to use the various <xref:System.Windows.DataObject.GetDataPresent%2A> method overloads to query whether a particular data format is present in a data object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab10-104">範例</span><span class="sxs-lookup"><span data-stu-id="cab10-104">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cab10-105">描述</span><span class="sxs-lookup"><span data-stu-id="cab10-105">Description</span></span>  
 <span data-ttu-id="cab10-106">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來查詢特定資料格式的描述項字串是否存在。</span><span class="sxs-lookup"><span data-stu-id="cab10-106">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%29> overload to query for the presence of a particular data format by descriptor string.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cab10-107">程式碼</span><span class="sxs-lookup"><span data-stu-id="cab10-107">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a><span data-ttu-id="cab10-108">範例</span><span class="sxs-lookup"><span data-stu-id="cab10-108">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cab10-109">描述</span><span class="sxs-lookup"><span data-stu-id="cab10-109">Description</span></span>  
 <span data-ttu-id="cab10-110">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.Type%29>多載來查詢特定資料格式由型別是否存在。</span><span class="sxs-lookup"><span data-stu-id="cab10-110">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.Type%29> overload to query for the presence of a particular data format by type.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cab10-111">程式碼</span><span class="sxs-lookup"><span data-stu-id="cab10-111">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a><span data-ttu-id="cab10-112">範例</span><span class="sxs-lookup"><span data-stu-id="cab10-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cab10-113">描述</span><span class="sxs-lookup"><span data-stu-id="cab10-113">Description</span></span>  
 <span data-ttu-id="cab10-114">下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>描述項字串的多載來查詢資料，並指定如何將自動轉換的資料格式。</span><span class="sxs-lookup"><span data-stu-id="cab10-114">The following example code uses the <xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29> overload to query for data by descriptor string, and specifying how to treat auto-convertible data formats.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cab10-115">程式碼</span><span class="sxs-lookup"><span data-stu-id="cab10-115">Code</span></span>  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a><span data-ttu-id="cab10-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cab10-116">See also</span></span>

- <xref:System.Windows.IDataObject>
