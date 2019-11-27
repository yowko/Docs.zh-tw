---
title: 存取層級
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
ms.openlocfilehash: 33a218a2acc3c876428d6c9a887280a559f84323
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348673"
---
# <a name="access-levels-in-visual-basic"></a>Visual Basic 中的存取層級

已宣告專案的*存取層級*是存取它的能力範圍，也就是有哪些程式碼有權讀取或寫入它。 這不只是由您宣告專案本身的方式所決定，也是由專案之容器的存取層級所決定。 無法存取包含專案的程式碼無法存取其包含的任何專案，即使是宣告為 `Public`的專案也一樣。 例如，您可以從包含結構的類別內部存取 `Private` 結構中的 `Public` 變數，而不是從該類別的外部進行存取。

## <a name="public"></a>公用

宣告語句中的[Public](../../../language-reference/modifiers/public.md)關鍵字會指定元素可以從相同專案中的程式碼、從參考專案的其他專案，以及從專案建立的任何元件中存取。 下列程式碼顯示範例 `Public` 宣告：

```vb
Public Class ClassForEverybody
```

您只能在模組、介面或命名空間層級使用 `Public`。 這表示您可以在來源檔案或命名空間層級，或在介面、模組、類別或結構中宣告公用元素，但不能在程式中宣告。
  
## <a name="protected"></a>受保護的

在宣告語句中， [Protected](../../../language-reference/modifiers/protected.md)關鍵字會指定只能從相同類別內或從這個類別衍生的類別來存取元素。 下列程式碼顯示範例 `Protected` 宣告：

```vb
Protected Class ClassForMyHeirs
```

只有當您宣告類別的成員時，才可以在類別層級使用 `Protected`。 這表示您可以在類別中宣告受保護的專案，但不能在來源檔案或命名空間的層級，或是在介面、模組、結構或程式內宣告。

## <a name="friend"></a>Friend

在宣告語句中， [Friend](../../../language-reference/modifiers/friend.md)關鍵字會指定專案可以從相同的元件中存取，但不能從元件外部存取。 下列程式碼顯示範例 `Friend` 宣告：

```vb
Friend stringForThisProject As String
```

您只能在模組、介面或命名空間層級使用 `Friend`。 這表示您可以在來源檔案或命名空間層級，或在介面、模組、類別或結構中宣告 friend 元素，但不能在程式中宣告。

## <a name="protected-friend"></a>Protected Friend

在宣告語句中，[受保護的 Friend](../../../language-reference/modifiers/protected-friend.md)關鍵字組合指定可以從衍生類別或從相同元件或兩者中存取專案。 下列程式碼顯示範例 `Protected Friend` 宣告：

```vb
Protected Friend stringForProjectAndHeirs As String
```

只有當您宣告類別的成員時，才可以在類別層級使用 `Protected Friend`。 這表示您可以在類別中宣告受保護的 friend 元素，但不能在來源檔案或命名空間的層級，或是在介面、模組、結構或程式內宣告。

## <a name="private"></a>私人

宣告語句中的[Private](../../../language-reference/modifiers/private.md)關鍵字會指定只能從相同的模組、類別或結構記憶體取元素。 下列程式碼顯示範例 `Private` 宣告：

```vb
Private _numberForMeOnly As Integer
```

您只能在模組層級使用 `Private`。 這表示您可以在模組、類別或結構中宣告私用專案，但不能在來源檔案或命名空間的層級、介面內或程式中宣告該元素。

在模組層級，不含任何存取層級關鍵字的 `Dim` 語句就相當於 `Private` 宣告。 不過，您可能會想要使用 `Private` 關鍵字，讓您的程式碼更容易閱讀和解讀。

## <a name="private-protected"></a>Private Protected

宣告語句中的[私用受保護](../../../language-reference/modifiers/private-protected.md)關鍵字組合，會指定元素只能從相同的類別中存取，也可以從與包含類別相同的元件中找到的衍生類別進行存取。 從 Visual Basic 15.5 開始支援 `Private Protected` 存取修飾詞。

下列範例顯示 `Private Protected` 宣告：

```vb
Private Protected internalValue As Integer
```

您只可以在類別內宣告 `Private Protected` 元素。 您不能在介面或結構內宣告它，也不能在來源檔案或命名空間層級（在介面或結構內）或程式中宣告它。

Visual Basic 15.5 和更新版本支援 `Private Protected` 存取修飾詞。 若要使用它，請將下列專案新增至您的 Visual Basic 專案（ *\*. vbproj*）檔案。 只要您的系統上已安裝 Visual Basic 15.5 或更新版本，它就可讓您利用最新版本的 Visual Basic 編譯器所支援的所有語言功能：

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

若要使用 `Private Protected` 的存取修飾詞，您必須將下列專案加入至您的 Visual Basic 專案（ *\*. vbproj*）檔案：

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。

## <a name="access-modifiers"></a>存取修飾詞

指定存取層級的關鍵字稱為*存取*修飾詞。 下表比較存取修飾詞：

|存取修飾詞|授與的存取層級|您可以使用此存取層級宣告的元素|宣告內容，您可以在其中使用此修飾詞|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|L<br /><br /> 任何可以看到公用專案的程式碼都可以存取它|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|來源檔案<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 執行個體<br /><br /> 結構|
|`Protected`|Derivational:<br /><br /> 類別中宣告受保護專案的程式碼，或從中衍生的類別，可以存取元素|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|執行個體|
|`Friend`|組件：<br /><br /> 宣告 friend 元素的元件中的程式碼可以存取它|介面<br /><br /> 模組<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|來源檔案<br /><br /> 命名空間<br /><br /> 介面<br /><br /> 模組<br /><br /> 執行個體<br /><br /> 結構|
|`Protected` `Friend`|`Protected` 和 `Friend`的聯集：<br /><br /> 相同類別或相同元件中的程式碼與受保護的 friend 元素相同，或在任何從專案類別衍生的類別中，都可以存取它|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|執行個體|
|`Private`|宣告內容：<br /><br /> 宣告私用專案之類型中的程式碼（包括包含的類型內的程式碼）可以存取元素|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 結構成員<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|模組<br /><br /> 執行個體<br /><br /> 結構|
|`Private Protected`|在類別中宣告私用受保護專案的程式碼，或在與 bas 類別相同的元件中找到的衍生類別中的程式碼。|介面<br /><br /> 類別<br /><br /> 結構<br /><br /> 程序<br /><br /> 屬性<br /><br /> 成員變數<br /><br /> 常數<br /><br /> 列舉<br /><br /> 事件<br /><br /> 外部宣告<br /><br /> 委派|執行個體|

## <a name="see-also"></a>另請參閱

- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [宣告項目名稱](declared-element-names.md)
- [對已宣告項目的參考](references-to-declared-elements.md)
- [宣告項目特性](declared-element-characteristics.md)
- [Visual Basic 中的存留期](lifetime.md)
- [Visual Basic 中的範圍](scope.md)
- [如何：控制變數的可用性](how-to-control-the-availability-of-a-variable.md)
- [變數](../variables/index.md)
- [變數宣告](../variables/variable-declaration.md)
