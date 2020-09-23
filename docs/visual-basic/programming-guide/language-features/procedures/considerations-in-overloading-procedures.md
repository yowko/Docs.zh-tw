---
title: 多載程序的考量
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 6197fa4041a22944542b2657e35bc293a6e5c244
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91075053"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a>多載化程序的考慮因素 (Visual Basic)

當您多載程式時，您必須針對每個多載版本使用 *不同的簽* 章。 這通常表示每個版本都必須指定不同的參數清單。 如需詳細資訊，請參閱程式多載 [中的](./procedure-overloading.md)「不同簽章」。  
  
 您可以使用程式來多載程式 `Function` `Sub` ，反之亦然，前提是它們具有不同的簽章。 兩個多載不能不同，因為它有傳回值，另一個則沒有。  
  
 您可以使用多載程式的相同方式來多載屬性，並具有相同的限制。 不過，您不能使用屬性來多載程式，反之亦然。  
  
## <a name="alternatives-to-overloaded-versions"></a>多載版本的替代專案  

 您有時會有多載版本的替代專案，特別是當引數的存在是選擇性的，或其數位為變數時。  
  
 請記住，並非所有語言都支援選擇性引數，而且參數陣列僅限於 Visual Basic。 如果您要撰寫的程式可能會從以數種不同語言撰寫的程式碼中呼叫，多載版本提供最大的彈性。  
  
### <a name="overloads-and-optional-arguments"></a>多載和選擇性引數  

 當呼叫程式碼可以選擇性地提供或省略一或多個引數時，您可以定義多個多載版本或使用選擇性參數。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載版本的時機  

 在下列情況下，您可以考慮定義一連串的多載版本：  
  
- 程式碼中的邏輯會根據呼叫程式碼是否提供選擇性引數而大幅不同。  
  
- 程式碼無法可靠地測試呼叫程式碼是否已提供選擇性引數。 例如，如果沒有任何可能的候選預設值，表示呼叫程式碼無法提供，就會發生這種情況。  
  
#### <a name="when-to-use-optional-parameters"></a>使用選擇性參數的時機  

 在下列情況下，您可能會想要使用一或多個選擇性參數：  
  
- 當呼叫程式碼未提供選擇性引數時，唯一必要的動作是將參數設定為預設值。 在這種情況下，如果您使用一或多個參數來定義單一版本，程式程式碼可能會比較複雜 `Optional` 。  
  
 如需詳細資訊，請參閱 [選用參數](./optional-parameters.md)。  
  
### <a name="overloads-and-paramarrays"></a>多載和 ParamArrays  

 當呼叫程式碼可以傳遞變數數目的引數時，您可以定義多個多載版本或使用參數陣列。  
  
#### <a name="when-to-use-overloaded-versions"></a>使用多載版本的時機  

 在下列情況下，您可以考慮定義一連串的多載版本：  
  
- 您知道呼叫程式碼永遠不會將較小的值傳遞給參數陣列。  
  
- 程式碼中的邏輯會根據呼叫程式碼所傳遞的值數目，而有很大的不同。  
  
- 呼叫程式碼可以傳遞不同資料類型的值。  
  
#### <a name="when-to-use-a-parameter-array"></a>使用參數陣列的時機  

 在下列情況下，參數會提供更好的服務 `ParamArray` ：  
  
- 您無法預測呼叫程式碼可以傳遞給參數陣列的值數目，也可以是大型數位。  
  
- 程式邏輯適合用來逐一查看呼叫程式碼所傳遞的所有值，基本上在每個值上執行相同的作業。  
  
 如需詳細資訊，請參閱 [參數陣列](./parameter-arrays.md)。  
  
## <a name="implicit-overloads-for-optional-parameters"></a>選擇性參數的隱含多載  

 具有 [選擇性](../../../language-reference/modifiers/optional.md) 參數的程式相當於兩個多載程式，一個具有選擇性參數，另一個則沒有。 您無法使用對應至其中一種的參數清單來多載這類程式。 下列宣告說明這一點。  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 針對具有多個選擇性參數的程式，會有一組隱含的多載，與前述範例中的邏輯類似。  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a>ParamArray 參數的隱含多載  

 編譯器會將具有 [ParamArray](../../../language-reference/modifiers/paramarray.md) 參數的程式視為具有無限數量的多載，這些多載在呼叫程式碼傳遞至參數陣列的情況下彼此不同，如下所示：  
  
- 當呼叫程式碼未提供引數給時，會有一個多載 `ParamArray`  
  
- 當呼叫程式碼提供專案類型的一維陣列時，會有一個多載 `ParamArray`  
  
- 針對每個正整數，當呼叫程式碼提供該數目的引數時，會有一個多載，每個 `ParamArray` 元素類型  
  
 下列宣告說明這些隱含多載。  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 您無法使用接受一維陣列作為參數陣列的參數清單來多載這類程式。 不過，您可以使用其他隱含多載的簽章。 下列宣告說明這一點。  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a>無程式設計為多載的替代方案  

 如果您想要允許呼叫程式碼將不同的資料類型傳遞給參數，替代方法是無型別的程式設計。 您可以 `Off` 使用 [Option Strict 語句](../../../language-reference/statements/option-strict-statement.md) 或 [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) 編譯器選項，將類型檢查參數設定為。 然後您不需要宣告參數的資料類型。 不過，相較于多載，此方法的缺點如下：  
  
- 無程式設計會產生效率不佳的執行程式碼。  
  
- 程式必須測試預期傳遞的每個資料類型。  
  
- 如果呼叫程式碼傳遞程式不支援的資料類型，則編譯器無法通知錯誤。  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [程序的疑難排解](./troubleshooting-procedures.md)
- [如何：定義程序的多個版本](./how-to-define-multiple-versions-of-a-procedure.md)
- [如何：呼叫多載程序](./how-to-call-an-overloaded-procedure.md)
- [如何：使用選擇性參數的多載程序](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [如何：多載使用不確定參數數目的程序](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [多載解析](./overload-resolution.md)
- [多載](../../../language-reference/modifiers/overloads.md)
