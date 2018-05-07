---
title: x:Subclass 指示詞
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b04982ff0b7685b4e4b809255e3bbe541b42cb9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xsubclass-directive"></a>x:Subclass 指示詞
修改 XAML 標記編譯行為時`x:Class`也會提供。 而不是建立部分類別，根據`x:Class`，提供`x:Class`建立為中繼類別，而且應該然後根據您提供的衍生的類別`x:Class`。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇性。 指定 CLR 命名空間包含`classname`。 如果`namespace`指定，則句點 （.） 分隔`namespace`和`classname`。|  
|`classname`|必要。 指定連接載入的 XAML 和程式碼後置該 XAML 的部分類別的 CLR 名稱。 請參閱＜備註＞。|  
|`subclassNamespace`|選擇性。 可能會不同於`namespace`如果每個命名空間可以解析其他。 指定 CLR 命名空間包含`subclassName`。 如果`subclassName`指定，則句點 （.） 分隔`subclassNamespace`和`subclassName`。|  
|`subclassName`|必要。 指定子類別的 CLR 名稱。|  
  
## <a name="dependencies"></a>相依性  
 [X:class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)也必須提供相同的物件，而該物件必須是在 XAML 生產的根項目。  
  
## <a name="remarks"></a>備註  
 `x:Subclass` 使用主要用於不支援部分類別宣告的語言。  
  
 做為類別`x:Subclass`不可為巢狀的類別，和`x:Subclass`必須參考根物件 「 相依性 」 一節中所述。  
  
 否則，概念的意義`x:Subclass`未定義的.NET Framework XAML 服務實作。 這是因為.NET Framework XAML 服務的行為未指定的 xaml 標記和支援的程式碼已連線的整體程式設計模型。 與相關的進一步概念實作`x:Class`和`x:Subclass`都是透過使用的程式設計模型或應用程式模型來定義如何連接 XAML 標記、 編譯的標記，並以 CLR 為基礎的程式碼後置的特定架構。 每個架構可能會有自己啟用的某些行為或在建置環境中必須包含的特定元件的建置動作。 在架構中，建置動作各有不同，根據特定 CLR 語言用於程式碼後置。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 `x:Subclass` 可以是頁面根或<xref:System.Windows.Application>在應用程式定義中，已經有根`x:Class`。 宣告`x:Subclass`網頁或應用程式的根目錄，或未指定它以外的任何項目上`x:Class`存在，會導致編譯時期錯誤。  
  
 建立衍生類別是否正確地為該工作`x:Subclass`案例是相當複雜。 您可能需要檢查中繼檔 （在 obj 資料夾，您的專案中編譯標記，其名稱中包含的.xaml 檔案名稱所產生的.g 檔案）。 這些中繼檔可協助您判斷在已編譯的應用程式中加入部分類別中的特定程式設計建構的來源。  
  
 在衍生類別中的事件處理常式必須是`internal override`(`Friend Overrides`在 Microsoft Visual Basic) 才能在編譯期間建立中繼類別中覆寫針對此處理常式的虛設常式。 否則衍生的類別實作會隱藏 （陰影） 的中繼類別實作，而且不會叫用的中繼類別處理常式。  
  
 當您同時定義`x:Class`和`x:Subclass`，您不需要提供任何實作類別所參考的`x:Class`。 您只需要提供給它透過名稱`x:Class`屬性，讓編譯器在有一些指導方針所建立的中繼檔案 （編譯器不會選取預設名稱在此情況下） 的類別。 您可以提供`x:Class`類別的實作; 不過，這不使用這兩個的典型範例`x:Class`和`x:Subclass`。  
  
## <a name="see-also"></a>另請參閱  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [WPF 的 XAML 和自訂類別](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
