---
title: "My.Resources 物件 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Resources
- My.Resources.MyResources.ResourceManager
- My.Resources.MyResources.Culture
dev_langs:
- VB
helpviewer_keywords:
- My.Resources object
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6ad5bd4e33438256719b59cb0936cf6bc8525ab1
ms.lasthandoff: 03/13/2017

---
# <a name="myresources-object"></a>My.Resources 物件
提供屬性和類別來存取應用程式的資源。  
  
## <a name="remarks"></a>備註  
 `My.Resources`物件提供的應用程式資源的存取權，並讓您動態擷取您的應用程式的資源。 如需詳細資訊，請參閱[管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources`物件會公開只有全域資源。 它不提供與表單相關聯的資源檔案的存取權。 您必須從表單存取表單資源。 如需詳細資訊，請參閱[逐步解說：將 Windows Forms 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)。  
  
 您可以存取應用程式的特定文化特性資源檔從`My.Resources`物件。 根據預設，`My.Resources`物件中查閱比對中的文化特性資源檔中的資源<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A>屬性。</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> 不過，您可以覆寫這個行為，並指定特定文化特性使用的資源。 如需詳細資訊，請參閱[桌面應用程式中的資源](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)。  
  
## <a name="properties"></a>屬性  
 屬性的`My.Resources`物件提供唯讀存取您的應用程式資源。 若要新增或移除資源，使用**專案設計工具**。 如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。 您可以存取資源，透過新增**專案設計工具**使用`My.Resources.``resourceName`。  
  
 您也可以新增或移除選取的專案中的資源檔**方案總管 中**，然後按一下**加入新項目**或**加入現有項目**從**專案**功能表。 您可以存取資源利用這種方式加入`My.Resources.``resourceFileName`。`resourceName`。  
  
 每個資源都有名稱、 類別目錄和值，以及這些資源設定會決定要存取資源的屬性會出現在`My.Resources`物件。 加入資源**專案設計工具**:  
  
-   名稱會決定屬性的名稱  
  
-   資源資料是屬性的值  
  
-   分類會決定屬性的型別︰  
  
|分類|屬性資料型別|  
|---|---|  
|**字串**|[String](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**映像**|<xref:System.Drawing.Bitmap></xref:System.Drawing.Bitmap>|  
|**圖示**|<xref:System.Drawing.Icon></xref:System.Drawing.Icon>|  
|**音訊**|<xref:System.IO.UnmanagedMemoryStream></xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>類別衍生自<xref:System.IO.Stream>類別，因此採用資料流，例如方法搭配<xref:Microsoft.VisualBasic.Devices.Audio.Play%2A>方法。</xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> </xref:System.IO.Stream> </xref:System.IO.UnmanagedMemoryStream>|  
|**檔案**|-   [字串](../../../visual-basic/language-reference/data-types/string-data-type.md)的文字檔案。<br />-<xref:System.Drawing.Bitmap>映像檔案。</xref:System.Drawing.Bitmap><br />-<xref:System.Drawing.Icon>的圖示檔案。</xref:System.Drawing.Icon><br />-<xref:System.IO.UnmanagedMemoryStream>音效檔。</xref:System.IO.UnmanagedMemoryStream>|  
|**其他**|在設計工具中的資訊來決定**類型**資料行。|  
  
## <a name="classes"></a>類別  
 `My.Resources`物件會公開為具有共用屬性的類別的每個資源檔。 類別名稱是資源檔的名稱相同。 上一節所述，在資源檔中的資源會公開為類別中的屬性。  
  
## <a name="example"></a>範例  
 本範例將表單的標題設定為指定的字串資源`Form1Title`應用程式資源檔中。 若要使用的範例，請應用程式必須具有名為的字串`Form1Title`其資源檔中。 如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。  
  
 [!code-vb[VbVbalrMyResources #&1;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## <a name="example"></a>範例  
 這個範例會將名為圖示表單的圖示`Form1Icon`均會儲存在應用程式的資源檔中。 範例能夠運作，如應用程式必須具有名為圖示`Form1Icon`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources #&2;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## <a name="example"></a>範例  
 本範例將表單的背景影像為指定的影像資源`Form1Background`，這是應用程式資源檔中。 讓範例能夠運作，應用程式必須有具名的影像資源`Form1Background`其資源檔中。  
  
 [!code-vb[VbVbalrMyResources #&3;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## <a name="example"></a>範例  
 此範例會播放的音效，儲存為音訊資源名為`Form1Greeting`應用程式的資源檔中。 範例能夠運作，如應用程式必須具有名為的音效資源`Form1Greeting`其資源檔中。 `My.Computer.Audio.Play`方法，僅適用於 Windows Form 應用程式。  
  
 [!code-vb[VbVbalrMyResources #&4;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## <a name="example"></a>範例  
 此範例會擷取字串資源的應用程式的法文文化特性版本。 資源名稱為`Message`。 若要變更文化特性的`My.Resources`物件使用，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。</xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>  
  
 這個範例能夠運作，如應用程式必須具有名為的字串`Message`其資源中檔案和應用程式應該具有該資源檔 Resources.fr FR.resx 法文文化特性版本。 如需詳細資訊，請參閱[How to︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)。 如果應用程式並沒有資源檔的法文文化特性版本`My.Resource`物件會從預設文化特性資源檔擷取資源。  
  
 [!code-vb[VbVbalrMyResources #&10;](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [如何︰ 加入或移除資源](http://msdn.microsoft.com/en-us/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [管理應用程式資源 (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-resources-dotnet)   
 [桌面應用程式中的資源](http://msdn.microsoft.com/library/8ad495d4-2941-40cf-bf64-e82e85825890)   
 [逐步解說︰ 將 Windows Form 當地語系化](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5)
