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
ms.openlocfilehash: c348d8fa2bd66a9abbb64c9363bb4dae0933ba34
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2019
ms.locfileid: "58047995"
---
# <a name="xsubclass-directive"></a>x:Subclass 指示詞
修改 XAML 標記編譯行為時`x:Class`也會提供。 而不是建立部分類別為基礎`x:Class`，提供`x:Class`會建立為中繼類別，並提供衍生的類別然後是根據預期`x:Class`。  
  
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
|`classname`|必要項。 指定的連接已載入的 XAML 和您程式碼後置的 XAML 的部分類別的 CLR 名稱。 請參閱＜備註＞。|  
|`subclassNamespace`|選擇性。 可能會不同於`namespace`如果每個命名空間可以解析其他。 指定 CLR 命名空間包含`subclassName`。 如果`subclassName`指定，則句點 （.） 分隔`subclassNamespace`和`subclassName`。|  
|`subclassName`|必要項。 指定的子類別的 CLR 名稱。|  
  
## <a name="dependencies"></a>相依性  
 [X:class 指示詞](x-class-directive.md)也必須提供相同的物件，而且該物件必須是 XAML 生產的根項目。  
  
## <a name="remarks"></a>備註  
 `x:Subclass` 使用方式，主要是用於不支援部分類別宣告的語言。  
  
 做為類別`x:Subclass`不能是巢狀的類別，和`x:Subclass`"Dependencies"區段中所述，必須指向根的物件。  
  
 否則，概念的意義`x:Subclass`未定義的.NET Framework XAML 服務實作。 這是因為.NET Framework XAML 服務的行為不會指定由哪一個 XAML 標記和備份程式碼連線的整體程式設計模型。 實作的進一步概念的相關`x:Class`和`x:Subclass`所使用的程式設計模型或應用程式模型來定義如何連接 XAML 標記，編譯過的標記，並以 CLR 為基礎的程式碼後置的特定架構執行。 每個架構可能會有自己的建置動作可讓某些行為或必須包含在建置環境的特定元件。 在架構中，建置動作也有所不同，根據特定的 CLR 語言用於程式碼後置。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 `x:Subclass` 可以在頁面根或在<xref:System.Windows.Application>在應用程式定義中，已有根`x:Class`。 宣告`x:Subclass`以外的頁面或應用程式的根，或未指定任何項目上`x:Class`存在，會造成編譯時期錯誤。  
  
 建立衍生類別可正確`x:Subclass`案例是相當複雜。 您可能需要檢查的中繼檔 （.g 標記編譯，其名稱中包含的.xaml 檔案名稱所產生您專案的 obj 資料夾中的資料檔案）。 這些中繼檔案可協助您判斷在編譯的應用程式中加入部分類別中的某些程式設計建構的原點。  
  
 在衍生類別中的事件處理常式必須是`internal override`(`Friend Overrides` Microsoft Visual Basic 中) 若要在編譯期間建立中繼類別中覆寫處理常式的虛設常式。 否則，衍生的類別實作隱藏 （陰影） 的中繼類別實作，而且中繼類別處理常式不會叫用。  
  
 當您定義這兩`x:Class`並`x:Subclass`，您不需要提供任何實作類別所參考的`x:Class`。 您只需要為它命名，以透過`x:Class`屬性，讓編譯器有一些類別，它會建立在中繼檔 （編譯器不會選取預設的名稱在此情況下） 中的指引。 您可以賦予`x:Class`類別的實作; 不過，這不是使用這兩個的典型案例`x:Class`和`x:Subclass`。  
  
## <a name="see-also"></a>另請參閱
- [x:Class 指示詞](x-class-directive.md)
- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
