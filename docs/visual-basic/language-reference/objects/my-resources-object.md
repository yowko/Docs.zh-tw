---
title: My.Resources 物件
ms.date: 07/20/2015
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
ms.openlocfilehash: 9fd23cb119ff9148a45d32ec70ccc4dad08ab876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="myresources-object"></a>My.Resources 物件
提供屬性和類別來存取應用程式的資源。  
  
## <a name="remarks"></a>備註  
 `My.Resources`物件提供存取應用程式的資源，並可讓您以動態方式擷取資源應用程式。 如需詳細資訊，請參閱[管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources`物件會公開只有全域資源。 它不提供與表單相關聯的資源檔案的存取權。 您必須在表單中存取的表單資源。  
  
 您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。 根據預設，`My.Resources`物件查閱比對中的文化特性資源檔中的資源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。 不過，您可以覆寫這個行為，並指定要用於資源的特定文化特性。 如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。  
  
## <a name="properties"></a>屬性  
 內容`My.Resources`物件提供唯讀存取您的應用程式資源。 若要新增或移除資源，使用**專案設計工具**。 您可以存取資源，透過新增**專案設計工具**使用`My.Resources.``resourceName`。  
  
 您也可以新增或移除選取的專案中的資源檔**方案總管 中**按一下**加入新項目**或**加入現有項目**從**專案**功能表。 您可以存取資源利用這個方式加入`My.Resources.``resourceFileName`、`resourceName`。  
  
 每個資源都有名稱、 類別目錄和值，以及這些資源的設定會決定要存取資源的屬性會出現在`My.Resources`物件。 資源中加入**專案設計工具**:  
  
-   名稱會決定屬性的名稱  
  
-   資源資料是屬性的值  
  
-   分類會決定屬性的型別：  
  
|分類|屬性資料型別|  
|---|---|  
|**字串**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**影像**|<xref:System.Drawing.Bitmap>|  
|**圖示**|<xref:System.Drawing.Icon>|  
|**音效**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別中，因此它可以搭配這些方法會採用資料流，例如<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。|  
|**檔案**|-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)文字檔案。<br />-   <xref:System.Drawing.Bitmap> 映像檔案。<br />-   <xref:System.Drawing.Icon> 圖示檔案。<br />-   <xref:System.IO.UnmanagedMemoryStream> 音效檔。|  
|**其他**|在設計工具中的資訊來決定**類型**資料行。|  
  
## <a name="classes"></a>類別  
 `My.Resources`物件會公開為具有共用的屬性類別的每個資源檔。 類別名稱是資源檔的名稱相同。 上一節所述，在資源檔中的資源會公開為類別中的屬性。  
  
## <a name="example"></a>範例  
 此範例會設定表單的標題為指定的字串資源`Form1Title`應用程式資源檔中。 如範例能夠運作，應用程式必須具有名為字串`Form1Title`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>範例  
 這個範例會將名為圖示表單的圖示`Form1Icon`儲存應用程式的資源檔。 如範例能夠運作，應用程式必須具有名為圖示`Form1Icon`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>範例  
 此範例會設定表單的背景影像的影像資源，名為`Form1Background`，這是應用程式資源檔中。 要讓範例能夠運作，應用程式必須具有名為的映像資源`Form1Background`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>範例  
 此範例會播放聲音儲存為具名的音效資源`Form1Greeting`應用程式的資源檔。 如範例能夠運作，應用程式必須具有名為的音訊資源`Form1Greeting`其資源檔中。 `My.Computer.Audio.Play`方法，僅適用於 Windows Forms 應用程式。  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>範例  
 這個範例會擷取字串資源的應用程式的法文文化特性版本。 資源名稱為`Message`。 若要變更文化特性的`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。  
  
 要讓範例能夠運作，應用程式必須具有名為字串`Message`中其資源檔和應用程式不能有該資源的檔案，Resources.fr FR.resx 法文文化特性版本。 如果應用程式並沒有法文文化特性的資源檔案版本，`My.Resource`物件會從預設文化特性資源檔擷取資源。  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)  
 [桌面應用程式中的資源](../../../framework/resources/index.md)  

