---
title: "My.Resources Object | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "My.Resources"
  - "My.Resources.MyResources.ResourceManager"
  - "My.Resources.MyResources.Culture"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Resources object"
ms.assetid: 34c3f2dc-7b87-432c-9d5f-17ea666bb266
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# My.Resources Object
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供屬性 \(Property\) 和類別，用以存取應用程式的資源。  
  
## 備註  
 `My.Resources` 物件會提供對應用程式資源的存取，並讓您動態擷取應用程式的資源。  如需詳細資訊，請參閱 [管理應用程式資源 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources` 物件只會公開 \(Expose\) 全域資源。  它不會提供與表單相關之資源檔的存取。  您必須從表單存取表單資源。  如需詳細資訊，請參閱[Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)。  
  
 您可以從 `My.Resources` 物件存取應用程式之文化特性 \(Culture\) 特有的資源檔。  根據預設，`My.Resources` 物件會在符合 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> 屬性內文化特性的資源檔中查詢資源。  不過，您可以覆寫這個行為，並指定要針對資源使用哪一個特定的文化特性。  如需詳細資訊，請參閱 [桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
## 屬性  
 `My.Resources` 物件的屬性提供對應用程式資源的唯讀存取。  若要新增或移除資源，請使用 \[**專案設計工具**\]。  如需詳細資訊，請參閱 [How to: Add or Remove Resources](http://msdn.microsoft.com/zh-tw/7b77bc06-3952-4799-b029-def3f8f7f88d)。  您可以使用 `My.Resources.``resourceName`，存取透過 \[**專案設計工具**\] 加入的資源。  
  
 您也可以用另一種方法新增或移除資源檔，此方法就是在 \[**方案總管**\] 中選取您的專案，然後按一下 \[**專案**\] 功能表中的 \[**加入新項目**\] 或 \[**加入現有項目**\]。  您可以使用 `My.Resources.``resourceFileName`.`resourceName`，存取透過這種方式加入的資源。  
  
 每個資源都會有一個名稱、分類和值，這些資源設定將會決定存取資源的屬性在 `My.Resources` 物件中的顯示方式。  若是在 \[**專案設計工具**\] 中加入的資源：  
  
-   名稱會決定屬性的名稱。  
  
-   資源資料即為屬性的值。  
  
-   分類會決定屬性的型別：  
  
|||  
|-|-|  
|分類|屬性資料型別|  
|**字串**|[字串](../../../visual-basic/language-reference/data-types/string-data-type.md)|  
|**影像**|<xref:System.Drawing.Bitmap>|  
|**圖示**|<xref:System.Drawing.Icon>|  
|**音訊**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> 由於 <xref:System.IO.UnmanagedMemoryStream> 類別衍生自 <xref:System.IO.Stream> 類別，所以它能和使用資料流的方法 \(如 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> 方法\) 一起使用。|  
|**檔案**|-   [String](../../../visual-basic/language-reference/data-types/string-data-type.md) 代表文字檔。<br />-   <xref:System.Drawing.Bitmap> 代表影像檔。<br />-   <xref:System.Drawing.Icon> 代表圖示檔。<br />-   <xref:System.IO.UnmanagedMemoryStream> 代表音效檔。|  
|**其他**|由設計工具之 \[**類型**\] 行中的資訊決定。|  
  
## 類別  
 `My.Resources` 物件會將每個資源檔公開為具有共用屬性的類別。  類別名稱會與資源檔的名稱相同。  如上節所述，資源檔中的資源會公開為類別中的屬性。  
  
## 範例  
 本範例將設定指定的字串資源的表單標題`Form1Title`應用程式資源檔中。  本範例正常執行，應用程式必須包含名為`Form1Title`在它的資源檔。  如需詳細資訊，請參閱 [How to: Add or Remove Resources](http://msdn.microsoft.com/zh-tw/7b77bc06-3952-4799-b029-def3f8f7f88d)。  
  
 [!code-vb[VbVbalrMyResources#1](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_1.vb)]  
  
## 範例  
 這個範例會將表單的圖示，設為應用程式資源檔中所儲存的圖示 \(名為 `Form1Icon`\)。  本範例正常執行，應用程式必須有名稱為一個圖示`Form1Icon`在它的資源檔。  
  
 [!code-vb[VbVbalrMyResources#2](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_2.vb)]  
  
## 範例  
 本範例將指定的影像資源設定表單的背景影像`Form1Background`，這是應用程式資源檔中。  本範例正常執行，應用程式必須影像資源名為`Form1Background`在它的資源檔。  
  
 [!code-vb[VbVbalrMyResources#3](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_3.vb)]  
  
## 範例  
 此範例會播放的音效，會儲存為具名的音效資源`Form1Greeting`應用程式的資源檔中。  本範例正常執行，應用程式必須有具名的音效資源`Form1Greeting`在它的資源檔。  `My.Computer.Audio.Play` 方法只適用於 Windows Form 應用程式。  
  
 [!code-vb[VbVbalrMyResources#4](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_4.vb)]  
  
## 範例  
 本範例擷取應用程式的字串資源的法文文化特性版本。  資源至名為`Message`。  若要變更的文化特性的`My.Resources`已使用的物件，此範例會使用<xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A>。  
  
 本範例正常執行，應用程式必須包含名為`Message`在它的資源檔，以及應用程式應該有該資源檔案中，Resources.fr FR.resx 的法文文化特性版本。  如需詳細資訊，請參閱 [How to: Add or Remove Resources](http://msdn.microsoft.com/zh-tw/7b77bc06-3952-4799-b029-def3f8f7f88d)。  如果應用程式並沒有法文文化特性的資源檔案版本， `My.Resource`物件會從預設文化特性資源檔中擷取資源。  
  
 [!code-vb[VbVbalrMyResources#10](../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/my-resources-object_5.vb)]  
  
## 請參閱  
 [How to: Add or Remove Resources](http://msdn.microsoft.com/zh-tw/7b77bc06-3952-4799-b029-def3f8f7f88d)   
 [管理應用程式資源 \(.NET\)](/visual-studio/ide/managing-application-resources-dotnet)   
 [桌面應用程式中的資源](../Topic/Resources%20in%20Desktop%20Apps.md)   
 [Walkthrough: Localizing Windows Forms](http://msdn.microsoft.com/zh-tw/9a96220d-a19b-4de0-9f48-01e5d82679e5)