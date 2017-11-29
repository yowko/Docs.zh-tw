---
title: "屬性程序 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbdf49d5c3eb5ef71b25a060d62f55f19098f445
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="property-procedures-visual-basic"></a>屬性程序 (Visual Basic)
屬性程序是一系列的[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]操作上模組、 類別或結構的自訂屬性的陳述式。 屬性程序也稱為是*屬性存取子*。  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]提供下列屬性程序：  
  
-   A`Get`程序會傳回屬性的值。 當您存取在運算式中的屬性時呼叫。  
  
-   A`Set`程序將屬性設定值，包括物件參考。 當您指派給屬性的值時呼叫。  
  
 您通常會在配對，使用中定義屬性程序`Get`和`Set`陳述式，但是您可以定義其中一個程序單獨如果屬性是唯讀狀態 ([Get 陳述式](../../../../visual-basic/language-reference/statements/get-statement.md)) 或唯寫 ([設定陳述式](../../../../visual-basic/language-reference/statements/set-statement.md))。  
  
 您可以省略`Get`和`Set`程序時使用的自動實作屬性。 如需詳細資訊，請參閱[自動實作的屬性](./auto-implemented-properties.md)。  
  
 您可以在類別、 結構和模組中定義屬性。 屬性是`Public`根據預設，這表示您可以從任何地方呼叫它們可以存取屬性的容器應用程式中。  
  
 如需屬性和變數的比較，請參閱[屬性之間的差異和 Visual Basic 中的變數](./differences-between-properties-and-variables.md)。  
  
## <a name="declaration-syntax"></a>宣告語法  
 所包圍的程式碼的區塊定義屬性本身[Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)和`End Property`陳述式。 在這個區塊中，每個屬性程序會顯示為一個宣告陳述式包圍的內部區塊 (`Get`或`Set`) 和比對`End`宣告。  
  
 宣告屬性和它的程序的語法如下所示：  
  
```  
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
  
 `Modifiers`可以以及屬性是否是唯讀或唯寫的指定存取層級和多載，覆寫、 共用和陰影的相關資訊。 `AccessLevel`上`Get`或`Set`程序可以是任何會比指定的屬性本身的存取層級更嚴格的層級。 如需詳細資訊，請參閱[Property 陳述式](../../../../visual-basic/language-reference/statements/property-statement.md)。  
  
### <a name="data-type"></a>資料類型  
 屬性的資料型別和主體的存取層級會定義在`Property`陳述式，不在屬性程序。 屬性可以有只有一個資料類型。 例如，您無法定義屬性，來儲存`Decimal`值，但擷取`Double`值。  
  
### <a name="access-level"></a>存取層級  
 不過，您可以定義主體的存取層級屬性，並進一步限制在一個屬性程序的存取層級。 例如，您可以定義`Public`屬性，然後定義`Private Set`程序。 `Get`程序會維持為`Public`。 您可以變更其中一個屬性程序的存取層級，而且您只可讓它更具限制性的主體的存取層級。 如需詳細資訊，請參閱[如何： 宣告混合存取層級的屬性](./how-to-declare-a-property-with-mixed-access-levels.md)。  
  
## <a name="parameter-declaration"></a>參數宣告  
 您每個參數宣告相同的方式[Sub 程序](./sub-procedures.md)，只不過您必須為傳遞機制`ByVal`。  
  
 參數清單中的每個參數的語法如下所示：  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 如果參數是選擇性的您也必須提供預設值做為其宣告的一部分。 指定預設值的語法如下所示：  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a>屬性值  
 在`Get`程序中，傳回值提供給屬性的值呼叫運算式。  
  
 在`Set`程序中，新的屬性值傳遞給參數`Set`陳述式。 如果您明確宣告的參數，您必須將它宣告使用相同的資料類型與屬性。 如果您未宣告的參數，則編譯器會使用隱含參數`Value`來代表要指派給屬性的新值。  
  
## <a name="calling-syntax"></a>呼叫語法  
 您叫用屬性程序以隱含方式進行屬性參考。 您將屬性的名稱使用相同的方式，您會使用變數的名稱，不同之處在於您必須提供值給不是選擇性的所有引數，您必須將引數清單括在括號中。 如果已不提供任何引數，您可以選擇性地省略括號。  
  
 語法隱含呼叫`Set`程序如下所示：  
  
 `propertyname[(argumentlist)] = expression`  
  
 語法隱含呼叫`Get`程序如下所示：  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a>宣告和呼叫的圖例  
 下列屬性會儲存為兩個構成的名稱、 名字和姓氏的完整名稱。 當呼叫程式碼讀取`fullName`、`Get`程序結合了兩個構成的名稱，並傳回的完整名稱。 當呼叫程式碼會指派新的完整名稱，`Set`程序會嘗試將它切為兩個構成的名稱。 如果找不到一個空格，則會儲存它全部都做為第一個名稱。  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 下列範例示範典型的屬性程序呼叫`fullName`。  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [程序](./index.md)  
 [函式程序](./function-procedures.md)  
 [運算子程序](./operator-procedures.md)  
 [程序參數和引數](./procedure-parameters-and-arguments.md)  
 [在 Visual Basic 中屬性和變數之間的差異](./differences-between-properties-and-variables.md)  
 [如何：建立屬性](./how-to-create-a-property.md)  
 [如何：呼叫屬性程序](./how-to-call-a-property-procedure.md)  
 [如何： 宣告及呼叫在 Visual Basic 中的預設屬性](./how-to-declare-and-call-a-default-property.md)  
 [如何：將值置入屬性](./how-to-put-a-value-in-a-property.md)  
 [如何：取得屬性值](./how-to-get-a-value-from-a-property.md)
