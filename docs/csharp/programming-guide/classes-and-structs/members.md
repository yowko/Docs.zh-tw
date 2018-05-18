---
title: 成員 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 61818b153bb74c5c0da053f381fd1ed9132c066b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="members-c-programming-guide"></a>成員 (C# 程式設計手冊)
類別和結構的成員可表示其資料與行為。 類別的成員包含在所有類別中宣告的成員，以及在其繼承階層架構之所有類別中宣告的所有成員 (建構函式和完成項除外)。 基底類別中的私用成員可繼承衍生類別，但卻無法從衍生類別進行存取。  
  
 下表列出類別或結構可以包含的成員類型：  
  
|成員|描述|  
|------------|-----------------|  
|[欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)|欄位是在類別範圍中宣告的變數。 欄位可以是內建的數字類型或其他類別的執行個體。 例如，行事曆類別可能包含目前日期的欄位。|  
|[常數](../../../csharp/programming-guide/classes-and-structs/constants.md)|常數是欄位或屬性，其值於編譯時期設定且無法變更。|  
|[屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)|屬性是類別上的方法，可供存取，就像類別上的欄位一樣。 屬性可以保護類別欄位，以免在物件不知情的情況下受到變更。|  
|[方法](../../../csharp/programming-guide/classes-and-structs/methods.md)|方法會定義類別可以執行的動作。 方法可接受參數以提供輸入資料，並藉由參數傳回輸出資料。 方法也可以不使用參數，直接傳回值。|  
|[事件](../../../csharp/programming-guide/events/index.md)|事件會提供發生次數的通知 (例如按鈕點選) 或針對其他物件成功完成方法的通知。 您可以使用委派來定義和觸發事件。|  
|[運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)|系統會將多載運算子視為類別成員。 當您多載運算子時，可將其定義為類別中的公用靜態方法。 系統不會將預先定義的運算子 (`+`、`*`、`<` 等等) 視為成員。 如需詳細資訊，請參閱[可多載的運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)。|  
|[索引子](../../../csharp/programming-guide/indexers/index.md)|索引子可讓您以類似陣列的方式來對物件進行索引。|  
|[建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)|建構函式是第一次建立物件時所呼叫的方法。 它們通常會用來初始化物件的資料。|  
|[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)|在 C# 中很少使用完成項。 完成項是即將從記憶體中移除物件時，由執行階段執行引擎所呼叫的方法。 它們通常用來確保任何必須發行的資源有受到妥善處理。|  
|[巢狀型別](../../../csharp/programming-guide/classes-and-structs/nested-types.md)|巢狀型別是在其他類型中宣告的類型。 如果某些類型包含物件，巢狀型別通常用於描述僅供該類型使用的這些物件。|  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)  
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [屬性](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [欄位](../../../csharp/programming-guide/classes-and-structs/fields.md)  
 [索引子](../../../csharp/programming-guide/indexers/index.md)  
 [事件](../../../csharp/programming-guide/events/index.md)  
 [巢狀型別](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
 [運算子](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [多載運算子](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)
