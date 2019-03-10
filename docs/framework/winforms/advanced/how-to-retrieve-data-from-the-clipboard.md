---
title: HOW TO：從剪貼簿擷取資料
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: 0ed79197190e9f646b5f94ff56e62b19fe4f366a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723851"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>HOW TO：從剪貼簿擷取資料
<xref:System.Windows.Forms.Clipboard>類別提供方法，您可以使用與 Windows 作業系統的剪貼簿功能互動。 許多應用程式資料做為暫存的儲存機制使用剪貼簿。 例如，文書處理器使用剪貼簿剪下和貼上作業期間。 也適用於將資訊傳送到另一個應用程式從剪貼簿。  
  
 有些應用程式會將資料儲存在剪貼簿中，多個格式增加可能可以使用這些資料的其他應用程式數目。 剪貼簿格式會是識別格式的字串。 使用已識別的格式的應用程式可以擷取剪貼簿上相關聯的資料。 <xref:System.Windows.Forms.DataFormats>類別會提供給您使用的預先定義的格式名稱。 您也可以使用您自己的格式名稱，或使用物件的類型作為其格式。 如需將資料加入至剪貼簿資訊，請參閱[How to:將資料加入至剪貼簿](how-to-add-data-to-the-clipboard.md)。  
  
 若要判斷 [剪貼簿] 是否包含以特定格式的資料，請使用其中一種`Contains`*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。 若要從剪貼簿擷取資料，請使用其中一種`Get`*格式*方法或<xref:System.Windows.Forms.Clipboard.GetData%2A>方法。 這些方法會在新[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
 存取資料，從剪貼簿，使用版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]，使用<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>方法呼叫的方法傳回的<xref:System.Windows.Forms.IDataObject>。 若要判斷是否可傳回之物件中特定的格式，例如，呼叫<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>方法。  
  
> [!NOTE]
>  所有以 Windows 為基礎的應用程式共用系統剪貼簿。 因此，內容會有所變更中是當您切換到另一個應用程式。  
>   
>  <xref:System.Windows.Forms.Clipboard>類別只能設定為單一執行緒 apartment (STA) 模式的執行緒中。 若要使用這個類別，請確認您`Main`方法會標示<xref:System.STAThreadAttribute>屬性。  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>若要從單一的常用格式剪貼簿擷取資料  
  
1.  使用<xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>， <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>， <xref:System.Windows.Forms.Clipboard.GetImage%2A>，或<xref:System.Windows.Forms.Clipboard.GetText%2A>方法。 （選擇性） 使用 對應`Contains`*格式*方法，以判斷是否有特定的格式資料。 這些方法都只[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>從剪貼簿中的自訂格式，擷取資料  
  
1.  使用<xref:System.Windows.Forms.Clipboard.GetData%2A>方法以自訂格式名稱。 這個方法是僅適用於[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]。  
  
     您也可以使用預先定義的格式名稱<xref:System.Windows.Forms.Clipboard.SetData%2A>方法。 如需詳細資訊，請參閱<xref:System.Windows.Forms.DataFormats>。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>若要從以多種格式剪貼簿 擷取資料  
  
1.  請使用 <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> 方法。 您必須使用這個方法來擷取資料，從剪貼簿上的版本早於[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>另請參閱
- [拖放作業和剪貼簿支援](drag-and-drop-operations-and-clipboard-support.md)
- [如何：將資料加入至剪貼簿](how-to-add-data-to-the-clipboard.md)
