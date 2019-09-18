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
ms.openlocfilehash: f6f02998a7648693bd731d6b2afdfd4499abaa04
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053903"
---
# <a name="xsubclass-directive"></a>x:Subclass 指示詞
當同時提供時`x:Class` ，修改 XAML 標記編譯行為。 除了建立以為基礎`x:Class`的部分類別，提供`x:Class`的會建立為中繼類別，然後您所提供的衍生類別`x:Class`應該會以為基礎。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">  
   ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇性。 指定包含`classname`的 CLR 命名空間。 如果`namespace`指定了, 則句點 (.) 會`namespace`分隔`classname`和。|  
|`classname`|必要項。 指定部分類別的 CLR 名稱, 此元件會連接已載入的 XAML 和該 XAML 的程式碼後置。 請參閱＜備註＞。|  
|`subclassNamespace`|選擇性。 如果每個命名`namespace`空間都可以解析另一個，則可以與不同。 指定包含`subclassName`的 CLR 命名空間。 如果`subclassName`指定了, 則句點 (.) 會`subclassNamespace`分隔`subclassName`和。|  
|`subclassName`|必要項。 指定子類別的 CLR 名稱。|  
  
## <a name="dependencies"></a>相依性  
 您也必須在相同的物件上提供[x：Class](x-class-directive.md)指示詞，而且該物件必須是 XAML 生產的根項目。  
  
## <a name="remarks"></a>備註  
 `x:Subclass`使用方式主要適用于不支援部分類別宣告的語言。  
  
 當做使用`x:Subclass`的類別不可以是嵌套類別，而且`x:Subclass`必須參考根物件，如「相依性」一節中所述。  
  
 否則，的概念意義`x:Subclass`會由 .NET Framework XAML 服務執行而未定義。 這是因為 .NET Framework XAML 服務行為並不會指定用來連接 XAML 標記和支援程式碼的整體程式設計模型。 與`x:Class` 和`x:Subclass`相關的進一步概念的執行，是由使用程式設計模型或應用程式模型的特定架構，來定義如何連接 XAML 標記、編譯的標記和 CLR 程式碼後置。 每個架構可能會有自己的組建動作，以啟用某些行為，或必須包含在組建環境中的特定元件。 在架構中，組建動作也會根據程式碼後置所使用的特定 CLR 語言而有所不同。  
  
## <a name="wpf-usage-notes"></a>WPF 使用注意事項  
 `x:Subclass`可以在頁面根目錄或應用程式定義中<xref:System.Windows.Application>的根目錄上，也就是已經有`x:Class`的。 在頁面或應用程式根目錄以外的任何專案上宣告，或指定不`x:Class`存在的專案，會導致編譯時期錯誤。 `x:Subclass`  
  
 建立可針對`x:Subclass`案例正常運作的衍生類別，相當複雜。 您可能需要檢查中繼檔案（在專案的 [obj] 資料夾中，透過標記編譯產生的. g 檔案，其中包含包含 .xaml 檔案名的名稱）。 這些中繼檔案可協助您判斷已編譯應用程式的聯結部分類別中，特定程式設計結構的來源。  
  
 衍生類別中的事件處理常式必須`internal override`是`Friend Overrides` （在 Microsoft Visual Basic 中），才能覆寫在編譯期間，在中繼類別中建立之處理常式的 stub。 否則，衍生的類別會隱藏（陰影）中繼類別的執行，而且不會叫用中繼類別處理常式。  
  
 當您同時`x:Class`定義和`x:Subclass`時，您不需要為所參考的`x:Class`類別提供任何實作為。 您只需要透過`x:Class`屬性指定名稱，編譯器就會針對它在中繼檔案中建立的類別提供一些指引（在此案例中，編譯器不會選取預設名稱）。 您可以為`x:Class`類別提供一個實作為，不過，這不是`x:Class`使用和`x:Subclass`的一般案例。  
  
## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](x-class-directive.md)
- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
