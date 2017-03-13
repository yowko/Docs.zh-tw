---
title: "固定大小緩衝區 (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "固定大小緩衝區 [C#]"
  - "unsafe 緩衝區 [C#]"
  - "unsafe 程式碼 [C#], 固定大小的緩衝區"
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# 固定大小緩衝區 (C# 程式設計手冊)
在 C\# 中，您可以使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式 \(Statement\)，在資料結構中建立具有固定大小陣列的緩衝區。  這個處理方式在使用現有的程式碼時會非常實用，例如，以其他語言撰寫的程式碼、已存在的 DLL 或 COM 專案。  固定的陣列可以帶有正規的結構成員所允許之任何屬性 \(Attribute\) 或修飾詞 \(Modifier\)。  唯一的限制是陣列型別 \(Array Type\) 必須為 `bool`、`byte`、 `char`、 `short`、`int`、`long`、`sbyte`、`ushort`、`uint`、`ulong`、`float` 或 `double`。  
  
```  
private fixed char name[30];  
```  
  
## 備註  
 在舊版 C\# 中，宣告 C\+\+ 樣式的固定大小結構是很困難的，因為包含陣列的 C\# 結構並不包含陣列元素。  而是，該結構包含項目的參考。  
  
 C\# 2.0 則加入了內嵌功能，當在 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 程式碼區塊中使用時，可將固定大小的陣列嵌入[結構](../../../csharp/language-reference/keywords/struct.md)內。  
  
 例如，在 C\# 2.0 之前，下列 `struct` 的大小為 8 位元組。  `pathName` 陣列是對堆積 \(Heap\) 配置陣列的參考：  
  
 [!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]  
  
 從 C\# 2.0 開始，`struct` 可以包含內嵌陣列。  在下列範例中，`fixedBuffer` 陣列有固定的大小。  若要存取陣列的項目，您可以使用 `fixed` 陳述式來建立第一個項目的指標。  `fixed` 陳述式會將 `fixedBuffer` 的執行個體固定至記憶體中的特定位置。  
  
 [!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]  
  
 有 128 個元素的 `char` 陣列大小為 256 個位元組。  無論編碼方式為何，在固定大小的 [char](../../../csharp/language-reference/keywords/char.md) 緩衝區中，每個字元都需要兩個位元組。  即使當字元緩衝區用 `CharSet = CharSet.Auto` 或 `CharSet = CharSet.Ansi` 封送處理至 API 方法或結構，算法也是一樣。  如需詳細資訊，請參閱 <xref:System.Runtime.InteropServices.CharSet>。  
  
 另一種常見的固定大小陣列就是 [bool](../../../csharp/language-reference/keywords/bool.md) 陣列。  `bool` 陣列中的項目其大小永遠為一個位元組。  `bool` 陣列並不適用於建立位元陣列或緩衝區。  
  
> [!NOTE]
>  除了使用 [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md) 建立的記憶體以外，C\# 編譯器和 Common Language Runtime \(CLR\) 並不執行任何安全性緩衝區滿溢 \(Buffer Overrun\) 檢查。  與使用其他 Unsafe 程式碼一樣，請小心使用。  
  
 Unsafe 緩衝區與正常陣列的差異之處如下：  
  
-   在 Unsafe 內容中只可使用 Unsafe 緩衝區。  
  
-   Unsafe 緩衝區一律為向量 \(即一維陣列\)。  
  
-   陣列的宣告應包含計數，例如 `char id[8]`。  您不可以使用 `char id[]`。  
  
-   在 Unsafe 內容中，Unsafe 緩衝區只能是結構的執行個體欄位。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)   
 [互通性](../../../csharp/programming-guide/interop/interoperability.md)