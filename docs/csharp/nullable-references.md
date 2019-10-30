---
title: 可為 Null 的參考型別
description: 本文提供可為 null 的參考型別總覽，已C#在8.0 中新增。 您會了解此功能如何為新及現有的專案，針對 Null 參考例外狀況提供安全。
ms.technology: csharp-null-safety
ms.date: 02/19/2019
ms.openlocfilehash: e20ea6efa389ba1aa0d8432a408c0b2a06a61c30
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039773"
---
# <a name="nullable-reference-types"></a>可為 Null 的參考型別

C# 8.0 引進**可為 Null 的參考型別**及**不可為 Null 的參考型別**，可讓您針對參考型別變數的屬性撰寫相關重要陳述式：

- **參考不應為 Null**。 當變數不應為 Null 時，編譯器會實施規則，確保對這些變數取值 (Dereference) 的過程是安全的，而不會事先檢查這些變數是不是 Null：
  - 變數必須初始化為非 Null 值。
  - 變數永遠不可指派 `null` 值。
- **參考可能為 Null**。 當變數可為 Null 時，編譯器會實施不同的規則，確保您已針對 Null 參考正確地進行檢查：
  - 只有在編譯器能保證該值並非為 Null 時，才能對該變數進行取值 (Dereference)。
  - 這些變數可使用預設的 `null` 值初始化，也可以在其他程式碼中指派 `null` 值。

相較於先前版本 C# 中處理參考變數的方式，這項新功能提供極大的好處，因為先前版本中無法從變數宣告判斷設計意圖。 編譯器不針對參考型別的 Null 參考例外狀況提供安全：

- **參考可為 Null**。 不會在參考型別初始化為 Null，或是稍後指派為 Null 時發出任何警告。
- **參考已假設為並非 Null**。 編譯器不會在對參考型別進行取值 (Dereference) 時發出任何警告。 (使用可為 Null 參考，編譯器會在您對可能為 Null 的變數進行取值 (Dereference) 時發出警告)。

透過新增的可為 Null 參考型別，您可以更清楚地宣告您的意圖。 `null` 值是表示變數並非指向某個值的正確方式。 請不要使用這項功能來從您的程式碼中移除所有 `null` 值。 相反地，您應該對編譯器及其他閱讀您程式碼之開發人員宣告您的意圖。 藉由宣告您的意圖，編譯器會在您撰寫的程式碼與該意圖不一致時通知您。

**可為 Null 參考型別**的語法與[可為 Null 實值型別](programming-guide/nullable-types/index.md)語法相同：將 `?` 附加至變數的型別。 例如，下列變數宣告代表可為 Null 字串變數，`name`：

```csharp
string? name;
```

任何沒有在型別名稱附加 `?` 的變數都是**不可為 Null 參考型別**。 這包含您啟用此功能時現有程式碼中所有的參考型別變數。

編譯器會使用靜態分析來判斷可為 Null 參考是否已知並非為 Null。 若您在可為 Null 參考可能為 Null 時對其進行取值 (Dereference)，編譯器會警告您。 您可以使用[null 容許運算子](language-reference/operators/null-forgiving.md)來覆寫此行為，`!` 遵循變數名稱。 例如，若您知道 `name` 變數並非為 Null，但編譯器卻發出警告，您可以撰寫下列程式碼來覆寫編譯器的分析：

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>型別的可 NULL 性

任何參考型別都可擁有四種「可 NULL 性」中的其中一種，其描述警告產生的時機：

- *不可為 null*： Null 無法指派給這個類型的變數。 此型別的變數不需進行 Null 檢查即可進行取值 (Dereference)。
- *Nullable*： null 可以指派給這個類型的變數。 若沒有事先檢查是否為 `null` 即對此型別的變數進行取值 (Dereference)，即會產生警告。
- *遺忘式*：這是C# 8.0 之前的狀態。 此型別的變數可進行取值或指派，且皆不會產生警告。
- *未知*：這通常適用于條件約束不會告知編譯器類型必須是可*為 null*或*不可為 null*的類型參數。

變數宣告中型別的可 NULL 性會由宣告該變數的「可為 Null 內容」控制。

## <a name="nullable-contexts"></a>可為 Null 內容

可為 Null 內容可讓您對編譯器解譯參考型別變數的方式進行細部控制。 任何指定之來源行的**可為 null 注釋內容**為已啟用或已停用。 您可以將C# 8.0 之前的編譯器視為在停用的可為 null 內容中編譯所有程式碼：任何參考型別都可以是 null。 可**為 null 警告內容**可能也會啟用或停用。 可為 Null 警告內容會指定編譯器使用其流程分析所產生的警告。

您可以使用 *.csproj*檔案中的 `Nullable` 元素，為專案設定可為 null 的注釋內容和可為 null 的警告內容。 此項目會設定編譯器解譯型別可 NULL 性的方式及所產生警告。 有效的設定如下：

- `enable`：可為 null 注釋內容已**啟用**。 可為 Null 警告內容為**啟用**。
  - 參考型別變數 (例如 `string`) 不可為 Null。  啟用所有可 NULL 性警告。
- `warnings`：可為 null 注釋內容已**停用**。 可為 Null 警告內容為**啟用**。
  - 參考型別變數為遺忘式。 啟用所有可 NULL 性警告。
- `annotations`：可為 null 注釋內容已**啟用**。 可為 Null 警告內容為**停用**。
  - 參考型別的變數（例如字串）不可為 null。 停用所有可 NULL 性警告。
- `disable`：可為 null 注釋內容已**停用**。 可為 Null 警告內容為**停用**。
  - 參考型別變數為遺忘式，與先前版本的 C# 相似。 停用所有可 NULL 性警告。

**範例**：

```xml
<Nullable>enable</Nullable>
```

您也可以使用指示詞，在您專案中的任何位置設定相同內容：

- `#nullable enable`：將可為 null 注釋內容和可為 null 警告內容設定為**已啟用**。
- `#nullable disable`：將可為 null 注釋內容和可為 null 警告內容設定為**停用**。
- `#nullable restore`：將可為 null 注釋內容和可為 null 警告內容還原至專案設定。
- `#nullable disable warnings`：將可為 null 警告內容設為**停用**。
- `#nullable enable warnings`：將可為 null 警告內容設定為 [**已啟用**]。
- `#nullable restore warnings`：將可為 null 警告內容還原至專案設定。
- `#nullable disable annotations`：將可為 null 注釋內容設定為**停用**。
- `#nullable enable annotations`：將可為 null 注釋內容設定為 [**已啟用**]。
- `#nullable restore annotations`：將批註警告內容還原至專案設定。

預設會**停用**可為 null 的注釋和警告內容。 這表示您現有的程式碼會在不變更的情況下編譯，而不會產生任何新的警告。

## <a name="nullable-annotation-context"></a>可為 Null 註釋內容

編譯器會在停用的可為 Null 註釋內容中使用下列規則：

- 您無法在停用的內容中宣告可為 Null 參考。
- 所有參考變數都可指派為 Null。
- 當對參考型別的變數進行取值 (Dereference) 時，不會產生任何警告。
- Null 容許運算子不可用於停用內容中。

行為與先前版本的 C# 相同。

編譯器會在啟用的可為 Null 註釋內容中使用下列規則：

- 參考型別的任何變數都是**不可為 Null 參考**。
- 任何不可為 Null 參考都可安全地進行取值 (Dereference)。
- 任何可為 Null 參考型別 (在變數宣告中的型別後方標註 `?`) 都可為 Null。 靜態分析會在對其進行取值 (Dereference) 時判斷該值是否已知並非為 Null。 若否，則編譯器會警告您。
- 您可以使用 Null 容許運算子來宣告可為 Null 參考並非為 Null。

在啟用的可為 Null 註釋內容中，`?` 字元會附加至宣告**可為 Null 參考型別**的參考型別。 **Null 容許運算子**`!` 可以附加至運算式，以宣告運算式不是 null。

## <a name="nullable-warning-context"></a>可為 Null 警告內容

可為 Null 警告內容與可為 Null 註釋內容不同。 即使停用新的註釋，仍可啟用警告。 編譯器會使用靜態分析來判斷任何參考的 **Null 狀態**。 當並未「停用」*可為 Null 警告內容*時，Null 狀態不是**並非為 Null**，就是**可能為 Null**。 若您在編譯器已判斷其**可能為 Null** 時對參考進行取值 (Dereference)，則編譯器會警告您。 除非編譯器可判斷下列兩個狀況的其中一種狀況，否則參考的狀態就會是**可能為 Null**：

1. 變數已確定指派為並非 Null 的值。
1. 變數或運算式已在取值 (Dereference) 之前針對 Null 進行檢查。

當可為 null 警告內容已啟用時，每當您以**可能為 null**的狀態來取值變數或運算式時，編譯器就會產生警告。 此外，當**可能的 null**變數或運算式指派給啟用的可為 null 注釋內容中的不可為 null 參考型別時，就會產生警告。

## <a name="see-also"></a>請參閱

- [草稿可為 null 參考類型規格](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [可為 Null 參考教學課程簡介](tutorials/nullable-reference-types.md)
- [將現有的程式碼基底遷移至可為 Null 參考](tutorials/upgrade-to-nullable-references.md)
