---
title: "指標類型 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "指標 [C#]"
  - "unsafe 程式碼 [C#], 指標"
ms.assetid: 3319faf9-336d-4148-9af2-1da2579cdd1e
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 指標類型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 unsafe 內容中，類型有可能是指標類型、實值類型或參考類型。  指標類型宣告會使用下列其中一種格式：  
  
```  
type* identifier;  
void* identifier; //allowed but not recommended  
```  
  
 下列任何一種類型都可能是指標類型：  
  
-   [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[char](../../../csharp/language-reference/keywords/char.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md)、[decimal](../../../csharp/language-reference/keywords/decimal.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md)。  
  
-   任何 [enum](../../../csharp/language-reference/keywords/enum.md) 類型。  
  
-   任何指標類型。  
  
-   任何只包含 Unmanaged 類型欄位的使用者定義結構類型。  
  
 指標類型不會從 [object](../../../csharp/language-reference/keywords/object.md) 繼承，而且指標類型與 `object` 之間無法進行轉換。  此外，boxing 和 unboxing 不支援指標。  不過，不同的指標類型之間以及指標類型與整數類資料類型之間可以進行轉換。  
  
 當您在相同的宣告中宣告多個指標時，星號 \(\*\) 只會與基礎類型一起出現，而不會做為每個指標名稱的前置詞使用。  例如：  
  
```  
int* p1, p2, p3;   // Ok  
int *p1, *p2, *p3;   // Invalid in C#  
```  
  
 指標無法指向參考或包含參考的[結構](../../../csharp/language-reference/keywords/struct.md)，因為即使指標指向物件參考，依然可以對物件參考進行記憶體回收。  記憶體回收行程不會持續追蹤是否有任何指標類型指向物件。  
  
 `myType*` 類型的指標變數值是 `myType` 類型變數的位址。  以下是指標類型宣告的範例：  
  
|範例|描述|  
|--------|--------|  
|`int* p`|`p` 為整數的指標。|  
|`int** p`|`p` 為整數指標的指標。|  
|`int*[] p`|`p` 為整數的一維陣列指標。|  
|`char* p`|`p` 為字元的指標。|  
|`void* p`|`p` 為未知類型的指標。|  
  
 您可以使用指標間接運算子 \* 存取指標變數所指向位置的內容。  例如，請參考下列宣告：  
  
```  
int* myVariable;  
```  
  
 這個運算式 `*myVariable` 表示位於 `myVariable` 所包含之位址的 `int` 變數。  
  
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)和[指標轉換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)主題中提供了一些指標範例。下列範例將示範 `unsafe` 關鍵字和 `fixed` 陳述式的需求，以及如何讓內部指標遞增。您可以將這個程式碼貼入主控台應用程式的 Main 函式中來執行它 \(記得在 \[**專案設計工具**\] 中啟用 Unsafe 程式碼、在功能表列上選擇 \[**專案**\]、\[**屬性**\]，然後選取 \[**組建**\] 索引標籤上的 \[**容許 Unsafe 程式碼**\]\)。  
  
```  
// Normal pointer to an object.  
int[] a = new int[5] {10, 20, 30, 40, 50};  
// Must be in unsafe code to use interior pointers.  
unsafe  
{  
    // Must pin object on heap so that it doesn't move while using interior pointers.  
    fixed (int* p = &a[0])  
    {  
        // p is pinned as well as object, so create another pointer to show incrementing it.  
        int* p2 = p;  
        Console.WriteLine(*p2);  
        // Incrementing p2 bumps the pointer by four bytes due to its type ...  
        p2 += 1;  
        Console.WriteLine(*p2);  
        p2 += 1;  
        Console.WriteLine(*p2);  
        Console.WriteLine("--------");  
        Console.WriteLine(*p);  
        // Deferencing p and incrementing changes the value of a[0] ...  
        *p += 1;  
        Console.WriteLine(*p);  
        *p += 1;  
        Console.WriteLine(*p);  
    }  
}  
  
Console.WriteLine("--------");  
Console.WriteLine(a[0]);  
Console.ReadLine();  
  
// Output:  
//10  
//20  
//30  
//--------  
//10  
//11  
//12  
//--------  
//12  
  
```  
  
 您無法將間接運算子套用至 `void*` 類型的指標。  不過，您可以使用轉型，將 Void 指標轉換成任何其他指標類型，反之亦然。  
  
 指標可以是 `null`。  將間接運算子套用至 null 指標會產生實作定義的行為。  
  
 請注意，在方法之間傳遞指標時，可能會導致未定義的行為。  例如，透過 Out 或 Ref 參數或做為函式結果傳回指向區域變數的指標。  如果已在固定區塊中設定指標，則該指標指向的變數就可能不再是固定的。  
  
 下表所列出的運算子和陳述式可以用於 unsafe 內容中的指標：  
  
|運算子\/陳述式|用途|  
|--------------|--------|  
|\*|執行指標間接取值。|  
|\-\>|透過指標存取結構的成員。|  
|\[\]|索引指標。|  
|`&`|取得變數位址。|  
|\+\+ 和 \-\-|遞增和遞減指標。|  
|\+ 和 \-|執行指標算術。|  
|\=\=、\!\=、\<、\>、\<\= 和 \>\=|比較指標。|  
|`stackalloc`|在堆疊上配置記憶體。|  
|`fixed` 陳述式|暫時固定變數以便找到其位址。|  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [指標轉換](../../../csharp/programming-guide/unsafe-code-pointers/pointer-conversions.md)   
 [指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)   
 [Boxing 和 Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md)