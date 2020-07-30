---
title: '處理 XML 檔案-c # 程式設計手冊'
description: '瞭解如何在 c # 程式設計中處理 XML 檔案。 請參閱程式碼範例，並查看其他可用的資源。'
ms.date: 07/20/2015
helpviewer_keywords:
- XML processing [C#]
- XML [C#], processing
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
ms.openlocfilehash: 6f8a278ed842cd9c4176f3efff423ee048f7e9b9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381537"
---
# <a name="process-the-xml-file-c-programming-guide"></a>處理 XML 檔案（c # 程式設計手冊）

編譯器會針對您的程式碼中標記為產生檔的每個結構，產生一個識別碼字串。 （如需如何標記程式碼的相關資訊，請參閱[建議的檔註解標記](./recommended-tags-for-documentation-comments.md)）。識別碼字串可唯一識別結構。 處理 XML 檔案的程式可以使用識別碼字串，來識別檔適用的對應 .NET 中繼資料或反映專案。

## <a name="id-strings"></a>識別碼字串

XML 檔案不是程式碼的階層式標記法。 它是一個一般清單，其中包含為每個元素產生的識別碼。

編譯器在產生識別碼字串時會遵守下列規則：

- 字串中沒有空白字元。

- 字串的第一個部分會使用單一字元並在後面加上冒號來識別成員的種類。 使用的成員類型如下：

    |字元|成員類型|注意|
    |---------------|-----------------|-|
    |N|namespace|您無法將文件註解新增至命名空間，但可讓 cref 參考它們 (如果支援)。|
    |T|type|型別可以是類別、介面、結構、列舉或委派。|
    |F|field|
    |P|屬性|包含索引子或其他索引的屬性。|
    |M|method|包含特殊方法，例如，構造函式和運算子。|
    |E|event|
    |!|錯誤字串|字串的其餘部分提供與錯誤相關的資訊。 C# 編譯器會針對無法解析的連結產生錯誤資訊。|

- 字串的第二個部分是項目的完整名稱 (從命名空間的根開始)。 項目名稱、其封入類型及命名空間會以句號來分隔。 如果項目名稱本身包含句點，則會以雜湊符號 ('#') 來取代它們。 假設沒有任何專案直接在其名稱中包含雜湊符號。 例如，字串構造函式的完整名稱是 "System.string. #ctor"。

- 若為屬性和方法，則後面會接著以括弧括住的參數清單。 如果沒有參數，則不會有括弧。 參數會以逗號分隔。 每個參數的編碼會直接遵循其在 .NET 簽章中的編碼方式：

  - 基底類型。 一般類型 (ELEMENT_TYPE_CLASS 或 ELEMENT_TYPE_VALUETYPE) 會表示為類型的完整名稱。

  - 內建類型（例如，ELEMENT_TYPE_I4、ELEMENT_TYPE_OBJECT、ELEMENT_TYPE_STRING、ELEMENT_TYPE_TYPEDBYREF 和 ELEMENT_TYPE_VOID）會表示為對應完整類型的完整名稱。 例如，System.Int32 或 System.TypedReference。

  - ELEMENT_TYPE_PTR 會表示為 '\*'，緊接在已修改的類型之後。

  - ELEMENT_TYPE_BYREF 會表示為 '\@'，緊接在已修改的類型之後。

  - ELEMENT_TYPE_PINNED 會表示為 '^'，緊接在已修改的類型之後。 C# 編譯器永遠都不會產生這個。

  - ELEMENT_TYPE_CMOD_REQ 會表示為 '&#124;' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。 C# 編譯器永遠都不會產生這個。

  - ELEMENT_TYPE_CMOD_OPT 會表示為 '!' 和修飾詞類別的完整名稱，緊接在已修改的類型之後。

  - ELEMENT_TYPE_SZARRAY 會表示為 "[]"，緊接在陣列的元素類型之後。

  - ELEMENT_TYPE_GENERICARRAY 會表示為 "[?]"，緊接在陣列的元素類型之後。 C# 編譯器永遠都不會產生這個。

  - ELEMENT_TYPE_ARRAY 會表示為 [*lowerbound*： `size` ，*lowerbound*： `size` ]，其中逗號數目是次序1，而每個維度的下限和大小（如果已知）則以十進位表示。 如果未指定下限或大小，則會省略。 如果省略了特定維度的下限和大小，也會省略 ':'。 例如，下限為 1 且未指定大小的 2 維度陣列是 [1:,1:]。

  - ELEMENT_TYPE_FNPTR 會表示為 "=FUNC:`type`(*signature*)"，其中 `type` 是傳回類型，而 *signature* 是方法的引數。 如果沒有任何引數，就會省略括弧。 C# 編譯器永遠都不會產生這個。

  下列簽章元件不會呈現，因為它們不會用來區別多載的方法：

  - 呼叫慣例

  - 傳回類型

  - ELEMENT_TYPE_SENTINEL

- 僅針對轉換運算子（ `op_Implicit` 和 `op_Explicit` ），方法的傳回值會編碼為 ' ~ '，後面接著傳回型別。

- 針對泛型類型，類型的名稱後面會接著反引號，然後是表示泛型類型參數數目的數字。 例如：

     ``<member name="T:SampleClass`2">`` 是類型的標籤，定義為 `public class SampleClass<T, U>`。

     針對採用泛型型別做為參數的方法，會將泛型型別參數指定為前面加上倒引號的數位（例如 \` 0、 \` 1）。 每個數位代表類型的泛型參數之以零為基底的陣列標記法。

## <a name="examples"></a>範例

下列範例顯示如何產生類別及其成員的識別碼字串：

[!code-csharp[csProgGuidePointers#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#21)]

## <a name="see-also"></a>另請參閱

- [C# 程式設計手冊](../index.md)
- [-doc （c # 編譯器選項）](../../language-reference/compiler-options/doc-compiler-option.md)
- [XML 文件註解](./index.md)
