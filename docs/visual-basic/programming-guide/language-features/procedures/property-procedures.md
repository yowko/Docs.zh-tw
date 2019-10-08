---
title: 屬性程序 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: f3b57ae45815fbd91cad17cddbed4d01037eb92f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002094"
---
# <a name="property-procedures-visual-basic"></a>屬性程序 (Visual Basic)
屬性程式是一系列的 Visual Basic 語句，可操作模組、類別或結構上的自訂屬性。 屬性程式也稱為*屬性存取*子。  
  
 Visual Basic 提供下列屬性程式：  
  
- @No__t-0 程式會傳回屬性的值。 當您存取運算式中的屬性時，就會呼叫它。  
  
- @No__t-0 程式會將屬性設定為值，包括物件參考。 當您將值指派給屬性時，就會呼叫它。  
  
 您通常會使用 `Get` 和 `Set` 語句來定義成對的屬性程式，但如果該屬性為唯讀（[Get 語句](../../../../visual-basic/language-reference/statements/get-statement.md)）或僅限寫入（[Set 語句](../../../../visual-basic/language-reference/statements/set-statement.md)），則可以單獨定義其中一個程式。  
  
 使用自動執行的屬性時，您可以省略 `Get` 和 @no__t 1 程式。 如需詳細資訊，請參閱[自動實作的屬性](./auto-implemented-properties.md)。  
  
 您可以在類別、結構和模組中定義屬性。 根據預設，屬性 @no__t 為0，這表示您可以從應用程式中可存取屬性容器的任何位置呼叫它們。  
  
 如需屬性和變數的比較，請參閱[Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)。  
  
## <a name="declaration-syntax"></a>宣告語法  
 屬性本身是由[屬性語句](../../../../visual-basic/language-reference/statements/property-statement.md)中包含的程式碼區塊和 `End Property` 語句所定義。 在此區塊內，每個屬性程式會顯示為包含在宣告語句內的內部區塊（`Get` 或 `Set`），以及相符的 `End` 宣告。  
  
 宣告屬性和其程式的語法如下：  
  
```vb  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 @No__t-0 可以指定有關多載、覆寫、共用和遮蔽的存取層級和資訊，以及屬性為唯讀或僅限寫入。 @No__t-1 或 @no__t 2 程式上的 `AccessLevel` 可以是比為屬性本身指定之存取層級更嚴格的任何層級。 如需詳細資訊，請參閱[Property 語句](../../../../visual-basic/language-reference/statements/property-statement.md)。  
  
### <a name="data-type"></a>資料類型  
 屬性的資料類型和主體存取層級是在 `Property` 語句中定義，而不是在屬性程式中。 屬性只能有一個資料類型。 例如，您無法定義屬性來儲存 `Decimal` 值，但會抓取 `Double` 值。  
  
### <a name="access-level"></a>存取層級  
 不過，您可以定義屬性的主體存取層級，並在其中一個屬性程式中進一步限制存取層級。 例如，您可以定義 `Public` 屬性，然後定義 @no__t 1 程式。 @No__t-0 程式仍然 `Public`。 您只能在其中一個屬性程式中變更存取層級，而且只能讓它比主要存取層級更嚴格。 如需詳細資訊，請參閱[如何：宣告具有混合存取層級 @ no__t-0 的屬性。  
  
## <a name="parameter-declaration"></a>參數宣告  
 您可以用與[Sub 程式](./sub-procedures.md)相同的方式宣告每個參數，但傳遞機制必須 `ByVal`。  
  
 參數清單中每個參數的語法如下：  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 如果參數是選擇性的，您也必須提供預設值做為其宣告的一部分。 指定預設值的語法如下：  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>屬性值  
 在 `Get` 程式中，傳回值會提供給呼叫運算式做為屬性的值。  
  
 在 `Set` 程式中，新的屬性值會傳遞給 `Set` 語句的參數。 如果您明確宣告參數，則必須使用與屬性相同的資料類型來宣告它。 如果您未宣告參數，編譯器會使用隱含參數 `Value` 來代表要指派給屬性的新值。  
  
## <a name="calling-syntax"></a>呼叫語法  
 藉由參考屬性，您可以隱含地叫用屬性程式。 使用屬性的名稱與使用變數名稱的方式相同，不同之處在于您必須為非選擇性的所有引數提供值，而且必須將引數清單括在括弧中。 如果未提供任何引數，您可以選擇性地省略括弧。  
  
 對 `Set` 程式之隱含呼叫的語法如下所示：  
  
 `propertyname[(argumentlist)] = expression`  
  
 對 `Get` 程式之隱含呼叫的語法如下所示：  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列屬性會將完整名稱儲存為兩個組成名稱、名字和姓氏。 當呼叫程式碼讀取 `fullName` 時，@no__t 1 程式會合並兩個組成名稱，並傳回完整名稱。 當呼叫程式碼指派新的完整名稱時，@no__t 0 程式會嘗試將它分成兩個組成的名稱。 如果找不到空間，則會將它全部儲存為名字。  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 下列範例顯示對 `fullName` 的屬性程式的一般呼叫。  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- [程序](./index.md)
- [函式程序](./function-procedures.md)
- [運算子程序](./operator-procedures.md)
- [程序參數和引數](./procedure-parameters-and-arguments.md)
- [Visual Basic 中的屬性和變數之間的差異](./differences-between-properties-and-variables.md)
- [如何：建立屬性 @ no__t-0
- [如何：呼叫屬性程式 @ no__t-0
- [如何：在 Visual Basic @ no__t-0 中宣告及呼叫預設屬性
- [如何：將值放在屬性 @ no__t-0 中
- [如何：從屬性 @ no__t-0 取得值
