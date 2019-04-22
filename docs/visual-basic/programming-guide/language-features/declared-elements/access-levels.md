---
title: Visual Basic 中的存取層級
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: d8f2f16d2fb15f2e840f13f177d3fea83fda315e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58843089"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic 中的存取層級
*存取層級*的宣告的項目能夠存取它的範圍，也就是哪些程式碼具有讀取或寫入其中的權限。 這決定不只您宣告的方式的項目本身，還包括的項目容器的存取層級。 無法存取包含的項目中的程式碼無法存取任何其包含的項目，即使是宣告為`Public`。 例如，`Public`變數中`Private`可以從存取結構，包含結構的類別內，而不是從該類別以外。  
  
## <a name="public"></a>Public  
 [公開](../../../../visual-basic/language-reference/modifiers/public.md)宣告陳述式中的關鍵字會指定從相同的專案中的任何位置的程式碼、 其他參考該專案的專案和專案所建立的任何組件，可存取項目。 下列程式碼顯示範例`Public`宣告。  
  
```vb  
Public Class classForEverybody  
```  
  
 您可以使用`Public`只能在模組、 介面或命名空間層級。 這表示您可以宣告在原始程式檔或命名空間，或介面、 模組、 類別或結構，但不是在程序層級的公用項目。  
  
## <a name="protected"></a>Protected  
 [受保護](../../../../visual-basic/language-reference/modifiers/protected.md)宣告陳述式中的關鍵字會指定只能從可以存取的項目，在相同類別中，或從衍生自這個類別的類別。 下列程式碼顯示範例`Protected`宣告。  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 您可以使用`Protected`只能在類別層級，以及僅當您宣告類別的成員。 這表示您可以宣告在類別中，但不是在原始程式檔或命名空間，或者介面、 模組、 結構或程序內的層級的受保護項目。  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)關鍵字宣告陳述式中的指定的項目可以存取從內相同的組件，而不是從外部組件。 下列程式碼顯示範例`Friend`宣告。  
  
```vb  
Friend stringForThisProject As String  
```  
  
 您可以使用`Friend`只能在模組、 介面或命名空間層級。 這表示您可以宣告 friend 項目層級的原始程式檔或命名空間，或介面、 模組、 類別或結構，但不是在程序。  
  
## <a name="protected-friend"></a>為 protected 的 Friend  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md)宣告陳述式中的關鍵字組合可讓您指定可以存取的項目，從衍生類別，或是從相同的組件，或兩者。 下列程式碼顯示範例`Protected Friend`宣告。  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 您可以使用`Protected Friend`只能在類別層級，以及僅當您宣告類別的成員。 這表示您可以宣告為 protected 的 friend 的項目在類別中，但不是在原始程式檔或命名空間，或者介面、 模組、 結構或程序內的層級。  
  
## <a name="private"></a>Private  
 [私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字宣告陳述式中的指定的項目可以存取只能從，在相同的模組、 類別或結構內。 下列程式碼顯示範例`Private`宣告。  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 您只能在模組層級使用 `Private`。 這表示您可以宣告私用項目內的模組、 類別或結構，但不是在原始程式檔或命名空間、 介面或程序中的層級。  
  
 在模組層級`Dim`而不需要任何存取層級關鍵字的陳述式相當於`Private`宣告。 不過，您可能想要使用`Private`關鍵字，讓您的程式碼更容易閱讀及解譯。  

## <a name="private-protected"></a>受保護的私用

[Private Protected](../../../language-reference/modifiers/private-protected.md)宣告陳述式中的關鍵字組合會指定項目可以存取只能從在相同類別中，以及從衍生類別中包含的類別相同的組件中找到。 `Private Protected`存取修飾詞支援從 Visual Basic 15.5 開始。

下列範例所示`Private Protected`宣告：

```vb
Private Protected internalValue As Integer
```

您可以宣告`Private Protected`只在類別內的項目。 您無法將其宣告中的介面或結構，也不可以宣告它的原始程式檔或命名空間、 介面或結構中，或在程序層級。

`Private Protected` Visual Basic 15.5 和更新版本支援的存取修飾詞。 若要使用它，您可以新增下列項目至 Visual Basic 專案 (*.vbproj) 檔。 只要 Visual Basic 15.5 或更新版本安裝在您的系統上，它可讓您充分利用所有最新版本的 Visual Basic 編譯器所支援的語言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

若要使用`Private Protected`存取修飾詞，您必須加入您的 Visual Basic 專案 (*.vbproj) 檔中的下列項目：

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定的 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。

## <a name="access-modifiers"></a>存取修飾詞  

指定存取層級的關鍵字稱為*存取修飾詞*。 下表比較存取修飾詞。  
  
|存取修飾詞|授與存取層級|您可以使用此存取層級宣告的項目|在其中您可以使用這個修飾詞宣告內容|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|不受限制：<br /><br /> 可以看到公用元素的任何程式碼可以存取它|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> Module<br /><br /> 類別<br /><br /> 結構|  
|`Protected`|衍生：<br /><br /> 宣告的受保護的項目或從其衍生的類別可以存取該項目之類別中的程式碼|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Friend`|組件︰<br /><br /> 宣告的 friend 項目可以存取它的組件中的程式碼|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|原始程式檔<br /><br /> 命名空間<br /><br /> 介面<br /><br /> Module<br /><br /> 類別<br /><br /> 結構|  
|`Protected` `Friend`|聯集之`Protected`和`Friend`:<br /><br /> 相同類別或相同的組件為受保護的 friend 項目，或在任何衍生自的項目類別的類別中的程式碼，可以存取它|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|  
|`Private`|宣告內容：<br /><br /> 在宣告私用項目內所包含的型別，包括程式碼的型別中的程式碼可以存取的項目|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|Module<br /><br /> 類別<br /><br /> 結構|
|`Private Protected`|在宣告私用的受保護項目，此類別中的程式碼或在 bas 類別相同的組件中找到的衍生類別中的程式碼。|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|類別|
  
## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [宣告項目名稱](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [在 Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [在 Visual Basic 中的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [如何：控制變數的可用性](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)
- [變數](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
