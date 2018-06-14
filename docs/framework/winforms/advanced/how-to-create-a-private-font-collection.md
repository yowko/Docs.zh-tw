---
title: 如何：建立私用字型集合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: 824d42c40b07e8662395e7a1286b9a5a6112c415
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523076"
---
# <a name="how-to-create-a-private-font-collection"></a>如何：建立私用字型集合
<xref:System.Drawing.Text.PrivateFontCollection>類別繼承自<xref:System.Drawing.Text.FontCollection>抽象基底類別。 您可以使用<xref:System.Drawing.Text.PrivateFontCollection>来維護一組專為您的應用程式的字型的物件。 私用字型集合可以包含已安裝的系統字型，以及在電腦尚未安裝的字型。 若要將字型檔案加入至私用字型集合中，呼叫<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A>方法<xref:System.Drawing.Text.PrivateFontCollection>物件。  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.PrivateFontCollection>物件包含的陣列<xref:System.Drawing.FontFamily>物件。  
  
 私用字型集合中的字型家族的數目不一定已加入至集合中的字型檔案的數目相同。 例如，假設您將 ArialBd.tff、 Times.tff 和 TimesBd.tff 檔案加入至集合。 會有三個檔案，但集合中的只有兩個系列因為 Times.tff 和 TimesBd.tff 屬於相同的系列。  
  
## <a name="example"></a>範例  
 下列範例會將在下列三個字型檔案<xref:System.Drawing.Text.PrivateFontCollection>物件：  
  
-   C:\\*systemroot*\Fonts\Arial.tff （新細明體，規則）  
  
-   C:\\*systemroot*\Fonts\CourBI.tff （： Courier New，粗體斜體)  
  
-   C:\\*systemroot*\Fonts\TimesBd.tff （新細明體，粗體顯示）  
  
 程式碼會擷取陣列<xref:System.Drawing.FontFamily>物件從<xref:System.Drawing.Text.FontCollection.Families%2A>屬性<xref:System.Drawing.Text.PrivateFontCollection>物件。  
  
 每個<xref:System.Drawing.FontFamily>物件在集合中，程式碼會呼叫<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>方法，以判斷是否有可用的各種樣式 （一般、 粗體、 斜體、 粗體斜體、 底線和刪除線）。 引數傳遞至<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>方法屬於<xref:System.Drawing.FontStyle>列舉型別。  
  
 如果指定的家族樣式組合功能<xref:System.Drawing.Font>物件建構使用該家族和樣式。 第一個引數傳遞至<xref:System.Drawing.Font.%23ctor%2A>建構函式是字型家族名稱 (不<xref:System.Drawing.FontFamily>物件適用於其他變化<xref:System.Drawing.Font.%23ctor%2A>建構函式)。 之後<xref:System.Drawing.Font>建構物件，它會傳遞至<xref:System.Drawing.Graphics.DrawString%2A>方法<xref:System.Drawing.Graphics>類別來顯示系列名稱，連同樣式的名稱。  
  
 下列程式碼的輸出與下圖中顯示的輸出相似。  
  
 ![字型文字](../../../../docs/framework/winforms/advanced/media/csfontstext7.png "csfontstext7")  
  
 Arial.tff （其中已加入至下列程式碼範例的私用字型集合） 是字型檔案，新細明體標準的樣式。 不過請注意，程式輸出會顯示數個可用樣式，而不是一般的新細明體字型系列。 這是因為[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以模擬粗體、 斜體和粗體斜體樣式，從標準的樣式。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 也可產生底線與 strikeouts 從標準的樣式。  
  
 同樣地，[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]可以模擬從粗體樣式或斜體樣式的粗體斜體樣式。 程式輸出顯示在即使 TimesBd.tff （新細明體，粗體顯示） 是唯一適用於時間系列粗體斜體樣式集合中的次檔案。  
  
 [!code-csharp[System.Drawing.FontsAndText#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 上述範例設計是為搭配 Windows Form 使用所設計，而且需要 <xref:System.Windows.Forms.PaintEventArgs> `e`，這是 <xref:System.Windows.Forms.PaintEventHandler> 的參數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Drawing.Text.PrivateFontCollection>  
 [使用字型和文字](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
