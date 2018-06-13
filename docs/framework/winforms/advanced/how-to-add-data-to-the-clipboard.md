---
title: 如何：將資料加入至剪貼簿
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 6002acfadfd0e688ef432baacbdabffb83890cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522063"
---
# <a name="how-to-add-data-to-the-clipboard"></a>如何：將資料加入至剪貼簿
<xref:System.Windows.Forms.Clipboard>類別提供可用來與 Windows 作業系統的剪貼簿功能互動的方法。 許多應用程式的資料做為暫存的儲存機制使用剪貼簿。 例如，文書處理器會使用剪貼簿剪下和貼上作業期間。 也適用於將資料傳送到另一個應用程式從剪貼簿。  
  
 當您將資料加入到剪貼簿時，您可以使其他應用程式可以辨識的資料，可以使用該格式表示的資料格式。 此外，您也可以將資料加入至剪貼簿中，多個不同的格式，可能可以使用這些資料的其他應用程式數目增加。  
  
 剪貼簿格式是字串，識別的格式，以便使用該格式的應用程式可以擷取相關聯的資料。 <xref:System.Windows.Forms.DataFormats>類別會提供貴用戶使用的預先定義的格式名稱。 您也可以使用您自己的格式名稱，或使用物件的類型作為其格式。  
  
 若要將資料加入至剪貼簿中一或多個格式，使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法。 您可以將任何物件傳遞至這個方法，但若要加入以多種格式的資料，您必須先將資料加入設計用於多種格式的個別物件。 一般而言，您將加入您的資料<xref:System.Windows.Forms.DataObject>，但是您可以使用實作的任何類型<xref:System.Windows.Forms.IDataObject>介面。  
  
 在[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]，您可以將資料直接加入剪貼簿使用設計來簡化基本剪貼簿工作的新方法。 當您使用單一、 共同的格式，例如文字的資料時，請使用這些方法。  
  
> [!NOTE]
>  所有的 Windows 應用程式共用剪貼簿。 因此，內容可能會變更當您切換到另一個應用程式。  
>   
>  <xref:System.Windows.Forms.Clipboard>類別只可以用於設定為單一執行緒 apartment (STA) 模式的執行緒。 若要使用這個類別，請確認您`Main`方法標示為<xref:System.STAThreadAttribute>屬性。  
>   
>  物件必須可序列化，才能放在剪貼簿上。 若要讓型別能夠進行序列化，將它與標記<xref:System.SerializableAttribute>屬性。 如果您將不可序列化的物件傳遞至剪貼簿方法時，該方法會失敗而不擲回例外狀況。 如需序列化的詳細資訊，請參閱 <xref:System.Runtime.Serialization>。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>若要將資料加入至剪貼簿中單一的一般格式  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetAudio%2A>， <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.SetImage%2A>，或<xref:System.Windows.Forms.Clipboard.SetText%2A>方法。 這些方法都只[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>若要將資料加入至剪貼簿中的自訂格式  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetData%2A>方法以自訂的格式名稱。 這個方法是僅適用於[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     您也可以使用具有預先定義的格式名稱<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>若要將資料加入至剪貼簿以多種格式  
  
1.  使用<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>方法並傳入<xref:System.Windows.Forms.DataObject>，其中包含您的資料。 您必須使用這個方法將資料加入至剪貼簿上的版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>另請參閱  
 [拖放作業和剪貼簿支援](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [操作說明：從剪貼簿擷取資料](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
