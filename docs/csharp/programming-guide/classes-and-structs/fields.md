---
title: 欄位 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 665c99302887c51c69b4d818619dd6bedd43b644
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714940"
---
# <a name="fields-c-programming-guide"></a>欄位 (C# 程式設計手冊)

「欄位」是任意類型的變數，可在[類別](../../language-reference/keywords/class.md)或[結構](../../language-reference/keywords/struct.md)中直接宣告。 欄位是其包含類型的「成員」。

類別或結構可能具有實例欄位、靜態欄位或兩者。 執行個體欄位是專屬於某種類型的執行個體。 如果您有搭配執行個體欄位 F 的類別 T，您可以建立兩個類型 T 的物件，然後修改每個物件中的 F 值，而不會影響另一個物件中的值。 相較之下，靜態欄位屬類別本身所擁有，並在該類別的所有執行個體之間共用。 您只能使用類別名稱來存取靜態欄位。 如果您依實例名稱存取靜態欄位，您會收到[CS0176](../../misc/cs0176.md)編譯時期錯誤。

一般而言，您應該只針對具有 private 或 protected 存取範圍的變數使用欄位。 您的類別公開給用戶端程式代碼的資料，應該透過[方法](./methods.md)、[屬性](./properties.md)和[索引子](../indexers/index.md)來提供。 藉由使用這些建構來間接存取內部欄位，即可防範無效的輸入值。 儲存由公用屬性公開之資料的私用欄位稱為「備份存放區」或「支援欄位」。

這些欄位通常會儲存必須可供多個類別方法存取的資料，以及其儲存時間必須比任何一個方法的存留期都還要長的資料。 例如，表示行事曆日期的類別可能會有三個整數欄位，分別代表月、日和年。 未在單一方法以外範圍使用的變數，應在方法主體本身內宣告為「區域變數」。

請依序指定欄位的存取層級、欄位的類型和欄位的名稱，以在類別區塊中宣告欄位。 例如：

[!code-csharp[csProgGuideObjects#61](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#61)]

若要存取物件中的欄位，請在物件名稱後面加上句號，再加上欄位的名稱，就像是 `objectname.fieldname`。 例如：

[!code-csharp[csProgGuideObjects#62](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#62)]

您可以在宣告欄位時，使用指派運算子來指定欄位的初始值。 例如，若要將 `day` 欄位自動指派為 `"Monday"`，您可以如下列範例所示宣告 `day`：

[!code-csharp[csProgGuideObjects#63](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#63)]

欄位會在呼叫物件執行個體的建構函式之前立即初始化。 如果建構函式指派了欄位的值，該值會覆寫欄位宣告期間所指定的任何值。 如需詳細資訊，請參閱[使用建構函式](./using-constructors.md)。

> [!NOTE]
> 欄位初始設定式無法參考其他執行個體欄位。

欄位可以標記為[public](../../language-reference/keywords/public.md)、 [private](../../language-reference/keywords/private.md)、 [protected](../../language-reference/keywords/protected.md)、 [internal](../../language-reference/keywords/internal.md)、 [protected internal](../../language-reference/keywords/protected-internal.md)或[private protected](../../language-reference/keywords/private-protected.md)。 這些存取修飾詞定義類別使用者如何存取欄位。 如需詳細資訊，請參閱[存取修飾詞](./access-modifiers.md)。

欄位可以選擇性地宣告為 [static](../../language-reference/keywords/static.md)。 這可隨時向呼叫者提供欄位，即使沒有任何類別執行個體存在。 如需詳細資訊，請參閱[靜態類別和靜態類別成員](./static-classes-and-static-class-members.md)。

欄位可以宣告為 [readonly](../../language-reference/keywords/readonly.md)。 您只能在初始化期間或在建構函式中指派值給唯讀欄位。 `static readonly` 欄位非常類似於常數，不同之處在於 C# 編譯器無法在編譯時期存取靜態唯讀欄位的值，只有在執行階段才能這麼做。 如需詳細資訊，請參閱[常數](./constants.md)。

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>請參閱

- [C# 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [使用建構函式](./using-constructors.md)
- [繼承](./inheritance.md)
- [存取修飾詞](./access-modifiers.md)
- [抽象和密封類別以及類別成員](./abstract-and-sealed-classes-and-class-members.md)
