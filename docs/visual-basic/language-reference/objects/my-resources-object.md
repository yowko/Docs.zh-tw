---
title: My.Resources 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: ee4d30b82ceada5c4f3fc4ad95dc8eeedd9355b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821734"
---
# <a name="myresources-object"></a>My.Resources 物件
提供屬性和類別來存取應用程式的資源。  
  
## <a name="remarks"></a>備註  
 `My.Resources`物件提供應用程式的資源的存取權，並讓您以動態方式擷取應用程式的資源。 如需詳細資訊，請參閱 <<c0> [ 管理的應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources`物件會公開僅有全域資源。 它不提供與表單相關聯的資源檔案的存取權。 您必須從表單來存取表單資源。  
  
 您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。 根據預設，`My.Resources`物件會比對中的文化特性的資源檔的資源查閱<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。 不過，您可以覆寫這個行為，並指定特定的文化特性，若要使用的資源。 如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。  
  
## <a name="properties"></a>屬性  
 屬性`My.Resources`物件提供唯讀存取您的應用程式資源。 若要新增或移除資源，請使用**專案設計工具**。 您可以存取透過新增的資源**專案設計工具**利用`My.Resources.` *resourceName*。  
  
 您也可以新增或移除選取的專案中的資源檔**方案總管**，然後按一下**加入新項目**或是**加入現有項目**從**專案**功能表。 您可以利用這個方式加入的資源`My.Resources.` *resourceFileName*`.`*resourceName*。  
  
 每個資源名稱、 類別和值，而且這些資源的設定可讓您決定要存取之資源的屬性會出現在`My.Resources`物件。 在 加入資源**專案設計工具**:  
  
-   名稱決定屬性的名稱  
  
-   資源資料是屬性的值  
  
-   類別會決定屬性的型別：  
  
|分類|屬性資料型別|  
|---|---|  
|**字串**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**影像**|<xref:System.Drawing.Bitmap>|  
|**圖示**|<xref:System.Drawing.Icon>|  
|**音效**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別中，因此它可以搭配方法，例如需要資料流，<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。|  
|**檔案**|-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)文字檔。<br />-   <xref:System.Drawing.Bitmap> 映像檔案。<br />-   <xref:System.Drawing.Icon> 圖示檔案。<br />-   <xref:System.IO.UnmanagedMemoryStream> 為音效檔。|  
|**其他**|由在設計工具中的資訊來判定**型別**資料行。|  
  
## <a name="classes"></a>類別  
 `My.Resources`物件會將每個資源檔公開為具有共用屬性的類別。 類別名稱是資源檔的名稱相同。 上一節所述，就會將資源檔中的資源公開為類別中的屬性。  
  
## <a name="example"></a>範例  
 本範例會將表單的標題為指定的字串資源`Form1Title`應用程式資源檔中。 針對此範例才能運作，應用程式必須具備名為一個字串`Form1Title`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>範例  
 此範例會將名為圖示表單的圖示`Form1Icon`均會儲存在應用程式的資源檔中。 針對此範例才能運作，應用程式必須具有名為圖示`Form1Icon`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>範例  
 此範例中設定的背景影像的表單名為映像資源`Form1Background`，這是應用程式資源檔中。 針對此範例正常運作，應用程式必須具有名為的映像資源`Form1Background`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>範例  
 此範例會播放聲音儲存為音訊的資源，名為`Form1Greeting`應用程式的資源檔中。 針對此範例才能運作，應用程式必須具有名為的音訊資源`Form1Greeting`其資源檔中。 `My.Computer.Audio.Play`方法是僅適用於 Windows Forms 應用程式。  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>範例  
 此範例會擷取字串資源的應用程式的法文文化特性版本。 資源名為`Message`。 若要變更文化特性所`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。  
  
 針對此範例正常運作，應用程式必須具備名為一個字串`Message`中其資源檔和應用程式應有的資源檔案，Resources.fr-FR.resx 法文文化特性版本。 如果應用程式並沒有法文文化特性的資源檔案版本，`My.Resource`物件會擷取預設文化特性資源檔中的資源。  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [桌面應用程式中的資源](../../../framework/resources/index.md)
