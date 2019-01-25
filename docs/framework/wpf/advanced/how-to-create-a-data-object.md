---
title: HOW TO：建立資料庫物件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataObject class [WPF], creating
- data objects [WPF], creating
- drag-and-drop [WPF], creating data objects
ms.assetid: 022fa142-717d-4fea-a53c-3b52e9d91aff
ms.openlocfilehash: edc301cb896dc8e704a0e17e8e22366d82cc0c17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687189"
---
# <a name="how-to-create-a-data-object"></a>HOW TO：建立資料庫物件
下列範例顯示建立資料物件，使用所提供的建構函式的各種方式<xref:System.Windows.DataObject>類別。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.Object%29>) 來初始化資料物件的字串。  在此情況下，根據儲存的資料類型自動決定適當的資料格式，並允許設定預設的已儲存資料進行自動轉換。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple)]  
  
### <a name="description"></a>描述  
 下列範例程式碼是如上所示的程式碼的精簡的版本。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_simple_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Simple_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_simple_condensed)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%29>) 來初始化字串與指定的資料格式的資料物件。  在此情況下的字串; 所指定的資料格式<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。 根據預設，允許使用的預存的資料進行自動轉換。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring)]  
  
### <a name="description"></a>描述  
 下列範例程式碼是如上所示的程式碼的精簡的版本。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_typestring_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_TypeString_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_typestring_condensed)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%2A>) 來初始化字串與指定的資料格式的資料物件。  在此情況下所指定的資料格式<xref:System.Type>參數。  根據預設，允許使用的預存的資料進行自動轉換。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type)]  
  
### <a name="description"></a>描述  
 下列範例程式碼是如上所示的程式碼的精簡的版本。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_type_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_Type_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_type_condensed)]  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例程式碼會建立新的資料物件，並使用其中一個多載的建構函式 (<xref:System.Windows.DataObject.%23ctor%28System.String%2CSystem.Object%2CSystem.Boolean%29>) 來初始化字串與指定的資料格式的資料物件。  在此情況下的字串; 所指定的資料格式<xref:System.Windows.DataFormats>類別提供一組預先定義的型別字串。 這個特定的建構函式多載可讓呼叫端指定是否允許自動轉換。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert)]  
  
### <a name="description"></a>描述  
 下列範例程式碼是如上所示的程式碼的精簡的版本。  
  
### <a name="code"></a>程式碼  
 [!code-csharp[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/CSharp/Window1.xaml.cs#_dragdrop_createdataobject_autoconvert_condensed)]
 [!code-vb[DragDrop_DragDropMiscCode#_DragDrop_CreateDataObject_AutoConvert_Condensed](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DragDrop_DragDropMiscCode/visualbasic/window1.xaml.vb#_dragdrop_createdataobject_autoconvert_condensed)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.IDataObject>
