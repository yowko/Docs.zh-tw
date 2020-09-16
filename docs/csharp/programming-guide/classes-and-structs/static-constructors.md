---
title: 靜態建構函式 - C# 程式設計手冊
description: 'C # 中的靜態函式會初始化靜態資料，或只在建立第一個實例或參考靜態成員之前執行一次動作。'
ms.date: 07/20/2015
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
ms.openlocfilehash: 1bb494ded34065bb76b72db40375555ca1eb6953
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541847"
---
# <a name="static-constructors-c-programming-guide"></a>靜態建構函式 (C# 程式設計手冊)
靜態建構函式用來初始化任何 [static](../../language-reference/keywords/static.md) 資料，或執行只需要執行一次的特定動作。 在建立第一個執行個體或參考任何靜態成員之前，會自動進行呼叫。  
  
 [!code-csharp[csProgGuideObjects#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#14)]  

## <a name="remarks"></a>備註
靜態建構函式具有下列屬性：  
  
- 靜態建構函式不會接受存取修飾詞，也不會包含參數。  

- 類別或結構只能有一個靜態建構函式。

- 靜態建構函式無法繼承或多載。

- 您無法直接呼叫靜態建構函式，且它是設計成只由通用語言執行平台 (CLR) 呼叫的。 系統會自動呼叫它。

- 使用者無法控制在程式中執行靜態建構函式的時間。
  
- 系統會在建立第一個執行個體或參考任何靜態成員之前，自動呼叫靜態建構函式來初始化 [class](../../language-reference/keywords/class.md)。 靜態建構函式會在執行個體建構函式之前執行。 當叫用指派給事件或委派的靜態方法，而不是指派給它時，會呼叫類型的靜態函式。 如果靜態欄位變數初始設定式存在於靜態建構函式的類別中，它們會按照出現的文字順序執行，緊接著執行靜態建構函式。

- 如果您未提供靜態的函式來初始化靜態欄位，則會將所有靜態欄位初始化為其預設值，如 [c # 類型的預設值](../../language-reference/builtin-types/default-values.md)所列。
  
- 如果靜態建構函式擲回例外狀況，執行階段不會叫用它第二次，而類型會在執行程式的應用程式定義域的存留期內保持未初始化。 在多數情況下，當靜態建構函示無法具現化型別時，或靜態建構函式內出現未處理的例外狀況時，會擲回 <xref:System.TypeInitializationException> 例外狀況。 對於在原始程式碼中未明確定義的隱含靜態建構函式，進行疑難排解可能需要檢查中繼語言 (IL) 程式碼。

- 靜態建構函式的存在可能阻止 <xref:System.Reflection.TypeAttributes.BeforeFieldInit> 型別屬性的新增。 這會限制執行階段最佳化。

- 宣告為 `static readonly` 的欄位，只能指派為其宣告的一部分，或在靜態建構函式中指派。 當不需要明確靜態建構函式時，請在宣告時初始化靜態欄位，而不要透過靜態建構函式，以獲得更好的執行階段最佳化。

> [!Note]
> 雖然無法直接存取明確靜態建構函式，但應記錄其存在，以協助對初始化例外狀況進行疑難排解。

### <a name="usage"></a>使用方式

- 靜態建構函式的一般用法為：當類別正在使用記錄檔，且建構函式用來將項目寫入這個檔案時。  
- 如果建構函式可以呼叫 `LoadLibrary` 方法，靜態建構函式在建立 unmanaged 程式碼的包裝函式類別時也很有用。  

- 靜態的函式也是在類型參數上強制執行執行時間檢查的方便位置，該參數無法在編譯時期透過條件約束 (類型參數條件約束) 來檢查。

## <a name="example"></a>範例
 在此範例中，`Bus` 類別具有靜態建構函式。 建立 `Bus` 的第一個執行個體 (`bus1`) 時，即會叫用靜態建構函式來初始化類別。 範例輸出可確認即使建立了兩個 `Bus` 執行個體，靜態建構函式也只執行一次，而且它是在執行個體建構函式執行之前執行。  
  
 [!code-csharp[csProgGuideObjects#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#15)]

## <a name="c-language-specification"></a>C# 語言規格
如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[靜態建構函式](~/_csharplang/spec/classes.md#static-constructors)一節。
  
## <a name="see-also"></a>另請參閱

- [C # 程式設計指南](../index.md)
- [類別和結構](./index.md)
- [建構函式](./constructors.md)
- [靜態類別和靜態類別成員](./static-classes-and-static-class-members.md)
- [完成項](./destructors.md)
- [建構函式設計指導方針](../../../standard/design-guidelines/constructor.md#type-constructor-guidelines)
- [安全性警告-CA2121：靜態的函式應為私用](/visualstudio/code-quality/ca2121-static-constructors-should-be-private)
