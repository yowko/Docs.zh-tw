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
ms.openlocfilehash: 2b7c82c31d2e31ccbf573cf1dfa138af2d99ce29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372451"
---
# <a name="myresources-object"></a>My.Resources 物件
提供用來存取應用程式資源的屬性和類別。  
  
## <a name="remarks"></a>備註  
 `My.Resources`物件提供應用程式資源的存取權，並可讓您以動態方式取得應用程式的資源。 如需詳細資訊，請參閱[管理應用程式資源（.net）](/visualstudio/ide/managing-application-resources-dotnet)。  
  
 `My.Resources`物件只會公開全域資源。 它不會提供與表單相關聯之資源檔的存取權。 您必須從表單存取表單資源。  
  
 您可以從物件存取應用程式的特定文化特性資源檔 `My.Resources` 。 根據預設， `My.Resources` 物件會從資源檔查閱符合屬性中文化特性的資源 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.UICulture%2A> 。 不過，您可以覆寫此行為，並指定要用於資源的特定文化特性。 如需詳細資訊，請參閱[桌面應用程式中的資源](../../../framework/resources/index.md)。  
  
## <a name="properties"></a>屬性  
 物件的屬性會 `My.Resources` 提供應用程式資源的唯讀存取權。 若要加入或移除資源，請使用 [**專案設計**工具]。 您可以使用 [資源設計工具] 來存取透過 [**專案設計**工具] 所新增的資源 `My.Resources.` * *。  
  
 您也可以在**方案總管**中選取您的專案，然後按一下 [**專案**] 功能表中的 [**加入新專案**] 或 [**加入現有專案**]，以加入或移除資源檔。 您可以使用 resourceFileName 資源，以這種方式存取新增的資源 `My.Resources.` *resourceFileName* `.` * *。  
  
 每個資源都有 [名稱]、[類別] 和 [值]，而這些資源設定會決定要如何存取資源的屬性會出現在 `My.Resources` 物件中。 針對在 [**專案設計**工具] 中新增的資源：  
  
- 名稱會決定屬性的名稱，  
  
- 資源資料是屬性的值。  
  
- 類別目錄會決定屬性的類型：  
  
|類別|屬性資料類型|  
|---|---|  
|**字串**|[String](../data-types/string-data-type.md)|  
|**影像**|<xref:System.Drawing.Bitmap>|  
|**圖示**|<xref:System.Drawing.Icon>|  
|**音訊**|<xref:System.IO.UnmanagedMemoryStream><br /><br /> <xref:System.IO.UnmanagedMemoryStream>類別衍生自 <xref:System.IO.Stream> 類別，因此可以搭配採用資料流程的方法（例如方法）使用 <xref:Microsoft.VisualBasic.Devices.Audio.Play%2A> 。|  
|**檔案儲存體**|-   文字檔的[字串](../data-types/string-data-type.md)。<br />-   <xref:System.Drawing.Bitmap>適用于影像檔案。<br />-   <xref:System.Drawing.Icon>適用于圖示檔。<br />-   <xref:System.IO.UnmanagedMemoryStream>適用于音效檔。|  
|**其他**|由設計工具的**類型**資料行中的資訊所決定。|  
  
## <a name="classes"></a>類別  
 物件會將 `My.Resources` 每個資源檔公開為具有共用屬性的類別。 類別名稱與資源檔的名稱相同。 如上一節所述，資源檔中的資源會公開為類別中的屬性。  
  
## <a name="example"></a>範例  
 這個範例會將表單的標題設定為 `Form1Title` 應用程式資源檔中名為的字串資源。 為了讓範例能夠正常執行，應用程式的資源檔中必須有一個名為的字串 `Form1Title` 。  
  
 [!code-vb[VbVbalrMyResources#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#1)]  
  
## <a name="example"></a>範例  
 這個範例會將表單的圖示設定為 `Form1Icon` 儲存在應用程式資源檔中名為的圖示。 為了讓範例正常執行，應用程式的資源檔中必須有一個名為的圖示 `Form1Icon` 。  
  
 [!code-vb[VbVbalrMyResources#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#2)]  
  
## <a name="example"></a>範例  
 這個範例會將表單的背景影像設定為名為的影像資源 `Form1Background` ，這是在應用程式資源檔中。 若要讓此範例能夠正常執行，應用程式必須 `Form1Background` 在其資源檔中具有名為的映射資源。  
  
 [!code-vb[VbVbalrMyResources#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#3)]  
  
## <a name="example"></a>範例  
 這個範例會在 `Form1Greeting` 應用程式的資源檔中播放儲存為音訊資源的音效。 為了讓範例能夠正常執行，應用程式的資源檔中必須有一個名為的音訊資源 `Form1Greeting` 。 `My.Computer.Audio.Play`方法僅適用于 Windows Forms 應用程式。  
  
 [!code-vb[VbVbalrMyResources#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#4)]  
  
## <a name="example"></a>範例  
 這個範例會抓取應用程式之字串資源的法文文化特性版本。 資源的名稱為 `Message` 。 為了變更物件所使用的文化特性 `My.Resources` ，此範例使用 <xref:Microsoft.VisualBasic.ApplicationServices.ApplicationBase.ChangeUICulture%2A> 。  
  
 為了讓此範例正常執行，應用程式的資源檔中必須有一個名為的字串 `Message` ，而應用程式應該具有該資源檔（Resources.fr-fr .resx）的法文文化特性版本。 如果應用程式沒有資源檔的法文文化特性版本， `My.Resource` 物件會從預設文化特性資源檔抓取資源。  
  
 [!code-vb[VbVbalrMyResources#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyResources/VB/Form1.vb#10)]  
  
## <a name="see-also"></a>另請參閱

- [管理應用程式資源 (.NET)](/visualstudio/ide/managing-application-resources-dotnet)
- [桌面應用程式中的資源](../../../framework/resources/index.md)
