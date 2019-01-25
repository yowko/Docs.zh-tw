---
title: HOW TO：判斷資料格式是否出現在資料物件中
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataFormats class [WPF]
- drag-and-drop [WPF], data formats present
- data formats [WPF], determining if present
ms.assetid: e487a454-c9fc-4e53-aeaa-c458d059ad4c
ms.openlocfilehash: 603ecf8945e461f281a49b430de8342c41203463
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546907"
---
# <a name="how-to-determine-if-a-data-format-is-present-in-a-data-object"></a>HOW TO：判斷資料格式是否出現在資料物件中
下列範例示範如何使用各種<xref:System.Windows.DataObject.GetDataPresent%2A>方法進行多載以查詢特定資料格式是否出現在資料物件。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%29>多載來查詢特定資料格式的描述項字串是否存在。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_string)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_String](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_string)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.Type%29>多載來查詢特定資料格式由型別是否存在。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_type)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼使用<xref:System.Windows.DataObject.GetDataPresent%28System.String%2CSystem.Boolean%29>描述項字串的多載來查詢資料，並指定如何將自動轉換的資料格式。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_querydataformats_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_QueryDataFormats_Autoconvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_querydataformats_autoconvert)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.IDataObject>
