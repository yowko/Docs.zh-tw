---
title: "固定大小緩衝區 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e1a3dcf953cb56fc3436fdd5e7ecb60478a12922
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a>固定大小緩衝區 (C# 程式設計手冊)
在 C# 中，您可以使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式，在資料結構中建立具有固定大小陣列的緩衝區。 當您使用現有的程式碼時，例如以其他語言撰寫的程式碼、既有的 Dll 或 COM 專案，這會很有用。 固定陣列可接受一般結構成員所允許的任何屬性或修飾詞。 唯一的限制是陣列類型必須為 `bool`、`byte`、`char`、`short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a>備註  
 在舊版 C# 中，因為包含陣列的 C# 結構並未包含陣列元素，所以很難宣告 C++ 樣式的固定大小結構。 相反地，該結構會包含元素的參考。  
  
 C# 2.0 新增一項功能，可將固定大小的陣列嵌入用於[不安全](../../../csharp/language-reference/keywords/unsafe.md)的程式碼區塊中的[結構](../../../csharp/language-reference/keywords/struct.md)。  
  
 例如，在 C# 2.0 之前，下列 `struct` 的大小會是 8 個位元組。 `pathName` 陣列是堆積配置陣列的參考：  
  
 [!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 從 C# 2.0 開始，`struct` 可以包含內嵌陣列。 在下列範例中，`fixedBuffer` 陣列具有固定大小。 若要存取陣列的元素，您可以使用 `fixed` 陳述式來建立第一個元素的指標。 `fixed` 陳述式會將 `fixedBuffer` 的執行個體固定在記憶體中的特定位置。  
  
 [!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 128 個元素的 `char` 陣列大小為 256 個位元組。 不論編碼為何，在固定大小的 [char](../../../csharp/language-reference/keywords/char.md) 緩衝區中，每個字元一律會有兩個位元組。 即使 char 緩衝區使用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構也一樣。 如需詳細資訊，請參閱<xref:System.Runtime.InteropServices.CharSet>。  
  
 另一個常見的固定大小陣列是 [bool](../../../csharp/language-reference/keywords/bool.md) 陣列。 `bool` 陣列中的元素大小一律為一個位元組。 `bool` 陣列不適用於建立位元陣列或緩衝區。  
  
> [!NOTE]
>  除了使用 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) 所建立的記憶體以外，C# 編譯器和 Common Language Runtime (CLR) 不會執行任何安全性緩衝區溢位檢查。 請與所有不安全的程式碼一樣小心使用。  
  
 不安全的緩衝區與一般陣列的差異如下：  
  
-   您只能在不安全的內容中使用不安全的緩衝區。  
  
-   不安全的緩衝區一律是向量或一維陣列。  
  
-   陣列的宣告應包含計數，例如 `char id[8]`。 您不能改用 `char id[]`。  
  
-   不安全的緩衝區只能是不安全內容中結構的執行個體欄位。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [不安全的程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [互通性](../../../csharp/programming-guide/interop/index.md)

