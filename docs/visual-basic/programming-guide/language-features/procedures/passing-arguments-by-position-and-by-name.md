---
title: 依位置和名稱傳遞引數 (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b872eda97d1e349ad781b12810e4b166d6e46fe1
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837308"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>依位置和名稱傳遞引數 (Visual Basic)
當您呼叫`Sub`或`Function`程序中，您可以傳遞引數*依位置*— 在程序的定義中的出現順序，或您可以將其傳遞*依名稱*，而不需要考慮位置。  
  
 當您依名稱傳遞引數時，您指定的引數宣告名稱後面加上冒號和等號 (`:=`)，後面接著引數值。 您可以提供以任何順序的具名引數。  
  
 例如，下列`Sub`程序會採用三個引數：  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 當您呼叫此程序時，您可以提供的引數依位置、 名稱，或使用兩者的混合。  
  
## <a name="passing-arguments-by-position"></a>依位置傳遞引數  
 您可以呼叫`Display`及其引數的方法依位置傳遞並以逗號分隔，如下列範例所示：  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 如果您省略選擇性的引數位置引數清單中，您必須保留它的位置，以逗點。 下列範例會呼叫`Display`方法，而不`age`引數：  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>依名稱傳遞引數  
 或者，您可以呼叫`Display`依名稱傳遞引數時，也以逗號分隔，如下列範例所示：  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 當您呼叫具有一個以上的選擇性引數的程序時，在這種方式中依名稱傳遞引數會特別有用。 如果您依名稱提供引數，您不必使用連續的逗號表示遺漏的位置引數。 依名稱傳遞引數也可讓您更輕鬆地追蹤您傳遞，並省略哪些哪一個引數。  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>混合位置和名稱引數  

下列範例所示，您可以提供引數位置和在單一程序呼叫中，名稱：  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 在上述範例中，沒有額外的逗號是為了保留位置省略`age`引數，因為`birth`依名稱傳遞。  
  
在 Visual basic 15.5 之前的版本，當您在混合位置和名稱、 位置引數所提供引數必須放在第一次。 一旦您依名稱提供引數，任何剩餘的引數必須全部是依名稱傳遞。  例如，下列呼叫來`Display`方法會顯示編譯器錯誤[BC30241:具名引數必須是](../../../misc/bc30241.md)。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

從 Visual Basic 15.5 開始，位置引數可以依照指定的引數如果結束的位置引數位於正確位置。 如果編譯 Visual Basic 15.5 中，先前的呼叫之下`Display`方法會編譯成功，並不會再產生編譯器錯誤[BC30241](../../../misc/bc30241.md)。  

當您想要使用具名引數，讓您的程式碼更容易閱讀，混合及比對任何順序中的具名和位置引數的這項功能會特別有用。 例如，下列`Person`類別建構函式需要兩個引數的型別`Person`，這兩者都可以是`Nothing`。 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

使用混合的具名和位置引數有助於進行程式碼的意圖清除時的值`father`並`mother`引數是`Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

若要依照使用具名引數的位置引數，必須將下列項目新增至您的 Visual Basic 專案 (\*.vbproj) 檔案：

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

如需詳細資訊，請參閱[設定的 Visual Basic 語言版本](../../../language-reference/configure-language-version.md)。

## <a name="restrictions-on-supplying-arguments-by-name"></a>依名稱提供引數的限制  

您無法將引數傳遞的名稱，以避免輸入必要的引數。 您可以省略的選擇性引數。  
  
您無法依名稱傳遞為參數陣列。 這是因為當您呼叫程序，您提供了不定數量的參數陣列中，以逗號分隔引數，而且編譯器無法將多個引數，與單一的名稱。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [如何：將引數傳遞至程序](./how-to-pass-arguments-to-a-procedure.md)
- [以傳值和傳址方式傳遞引數](./passing-arguments-by-value-and-by-reference.md)
- [選擇性參數](./optional-parameters.md)
- [參數陣列](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
