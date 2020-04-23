---
title: 可為 Null 的參考型別
description: 本文概述了在 C# 8.0 中添加的可無引用類型。 您會了解此功能如何為新及現有的專案，針對 Null 參考例外狀況提供安全。
ms.technology: csharp-null-safety
ms.date: 04/21/2020
ms.openlocfilehash: 589118ffaa9ad39f000e3e5adf2896d114f68dd3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101968"
---
# <a name="nullable-reference-types"></a>可為 Null 的參考型別

C# 8.0 引進**可為 Null 的參考型別**及**不可為 Null 的參考型別**，可讓您針對參考型別變數的屬性撰寫相關重要陳述式：

- **參考不應為空**。 當變數不應該是 null 時,編譯器將強制實施規則,以確保無需首先檢查這些變數是否為空即可安全地取消引用這些變數:
  - 變數必須初始化為非 Null 值。
  - 變數永遠不可指派 `null` 值。
- **參考可能為 Null**。 當變數可為 Null 時，編譯器會實施不同的規則，確保您已針對 Null 參考正確地進行檢查：
  - 只有在編譯器能保證該值並非為 Null 時，才能對該變數進行取值 (Dereference)。
  - 這些變數可使用預設的 `null` 值初始化，也可以在其他程式碼中指派 `null` 值。

此新功能與早期 C# 版本中的引用變數的處理具有顯著優勢,因為無法從變數聲明確定設計意圖。 編譯器不針對參考型別的 Null 參考例外狀況提供安全：

- **參考可為 Null**。 當引用類型初始化為 null 或稍後分配給 null 時,編譯器不會發出警告。 當取消引用這些變數而不進行空檢查時,編譯器會發出警告。
- **參考已假設為並非 Null**。 編譯器不會在對參考型別進行取值 (Dereference) 時發出任何警告。 如果變數設置為可能為空的運算式,編譯器將發出警告。

這些警告在編譯時發出。 編譯器不會在空上下文中添加任何空檢查或其他運行時構造。 在運行時,可空引用和非空引用等效。

透過新增的可為 Null 參考型別，您可以更清楚地宣告您的意圖。 `null` 值是表示變數並非指向某個值的正確方式。 請不要使用這項功能來從您的程式碼中移除所有 `null` 值。 相反地，您應該對編譯器及其他閱讀您程式碼之開發人員宣告您的意圖。 藉由宣告您的意圖，編譯器會在您撰寫的程式碼與該意圖不一致時通知您。

**可為 Null 參考型別**的語法與[可為 Null 實值型別](language-reference/builtin-types/nullable-value-types.md)語法相同：將 `?` 附加至變數的型別。 例如，下列變數宣告代表可為 Null 字串變數，`name`：

```csharp
string? name;
```

沒有附加為類型`?`名稱的任何變數,**都是無法空的參考型態**。 這包括啟用此功能的現有代碼中的所有引用類型變數。

編譯器會使用靜態分析來判斷可為 Null 參考是否已知並非為 Null。 若您在可為 Null 參考可能為 Null 時對其進行取值 (Dereference)，編譯器會警告您。 可以使用變數名稱後使用 null[寬容運算符](language-reference/operators/null-forgiving.md)`!`來重寫此行為。 例如，若您知道 `name` 變數並非為 Null，但編譯器卻發出警告，您可以撰寫下列程式碼來覆寫編譯器的分析：

```csharp
name!.Length;
```

## <a name="nullability-of-types"></a>型別的可 NULL 性

任何參考型別都可擁有四種「可 NULL 性」** 中的其中一種，其描述警告產生的時機：

- *無法為空*:無法將 Null 分配給此類型的變數。 此型別的變數不需進行 Null 檢查即可進行取值 (Dereference)。
- *空*:可以為此類型的變數分配 null。 若沒有事先檢查是否為 `null` 即對此型別的變數進行取值 (Dereference)，即會產生警告。
- *遺忘*:遺忘是 C# 8.0 前狀態。 此型別的變數可進行取值或指派，且皆不會產生警告。
- *未知*: 未知通常是類型參數,其中不解譯器類型必須*為空*或*無法為空*。

變數宣告中型別的可 NULL 性會由宣告該變數的「可為 Null 內容」** 控制。

## <a name="nullable-contexts"></a>可為 Null 內容

可為 Null 內容可讓您對編譯器解譯參考型別變數的方式進行細部控制。 開啟或關閉任何給定源行的**空註解上下文**。 您可以將前 C_ 8.0 編譯器視為在禁用的可空上下文中編譯所有代碼:任何引用類型可能為空。 也可以開啟或關閉**可取消的警告上下文**。 可為 Null 警告內容會指定編譯器使用其流程分析所產生的警告。

可以使用`Nullable`*.csproj*檔中的元素為專案設置可無效的註釋上下文和空警告上下文。 此項目會設定編譯器解譯型別可 NULL 性的方式及所產生警告。 有效的設定如下：

- `enable`:**啟用**了空註解上下文。 可為 Null 警告內容為**啟用**。
  - 參考型別變數 (例如 `string`) 不可為 Null。  啟用所有可 NULL 性警告。
- `warnings`:禁用了空註釋**上下文。** 可為 Null 警告內容為**啟用**。
  - 參考型別變數為遺忘式。 啟用所有可 NULL 性警告。
- `annotations`:**啟用**了空註解上下文。 可為 Null 警告內容為**停用**。
  - 引用類型的變數(例如字串)是不可虛無的。 停用所有可 NULL 性警告。
- `disable`:禁用了空註釋**上下文。** 可為 Null 警告內容為**停用**。
  - 參考型別變數為遺忘式，與先前版本的 C# 相似。 停用所有可 NULL 性警告。

**範例**：

```xml
<Nullable>enable</Nullable>
```

您也可以使用指示詞，在您專案中的任何位置設定相同內容：

- `#nullable enable`:將可開啟的註解上下文與空警告上下文設定**為 開啟**。
- `#nullable disable`:將可關閉的註解上下文與空警告上下文設定為**關閉**。
- `#nullable restore`:將可無效註釋上下文和空警告上下文還原到項目設置。
- `#nullable disable warnings`:將不合法的警告的文字設定為**關閉**。
- `#nullable enable warnings`:將可開啟的警告上下文設定為**啟用**。
- `#nullable restore warnings`:將可無效的警告上下文還原到項目設置。
- `#nullable disable annotations`:將可關閉的註解上下文設定為**關閉**。
- `#nullable enable annotations`:將可開啟的註解上下文設定為**啟用**。
- `#nullable restore annotations`:將註釋警告上下文還原到項目設置。

默認情況下,將**禁用**可作註釋和警告上下文,包括新專案。 這意味著您的現有代碼無需更改,也沒有生成任何新警告。

這些選項提供了兩個不同的策略來[更新現有代碼庫](nullable-migration-strategies.md)以使用空引用類型。

## <a name="nullable-annotation-context"></a>可為 Null 註釋內容

編譯器會在停用的可為 Null 註釋內容中使用下列規則：

- 您無法在停用的內容中宣告可為 Null 參考。
- 可以為所有引用變數分配一個 null 值。
- 當對參考型別的變數進行取值 (Dereference) 時，不會產生任何警告。
- Null 容許運算子不可用於停用內容中。

行為與先前版本的 C# 相同。

編譯器會在啟用的可為 Null 註釋內容中使用下列規則：

- 參考型別的任何變數都是**不可為 Null 參考**。
- 任何不可為 Null 參考都可安全地進行取值 (Dereference)。
- 任何可為 Null 參考型別 (在變數宣告中的型別後方標註 `?`) 都可為 Null。 靜態分析確定在取消引用時,該值是否已知為非空值。 若否，則編譯器會警告您。
- 您可以使用 Null 容許運算子來宣告可為 Null 參考並非為 Null。

在啟用的可為 Null 註釋內容中，`?` 字元會附加至宣告**可為 Null 參考型別**的參考型別。 **可以將放棄運算符**`!`追加到表達式中,以聲明表達式不為空。

## <a name="nullable-warning-context"></a>可為 Null 警告內容

可為 Null 警告內容與可為 Null 註釋內容不同。 即使停用新的註釋，仍可啟用警告。 編譯器會使用靜態分析來判斷任何參考的 **Null 狀態**。 當並未「停用」*****可為 Null 警告內容*時，Null 狀態不是**並非為 Null**，就是**可能為 Null**。 若您在編譯器已判斷其**可能為 Null** 時對參考進行取值 (Dereference)，則編譯器會警告您。 除非編譯器可判斷下列兩個狀況的其中一種狀況，否則參考的狀態就會是**可能為 Null**：

1. 變數已確定指派為並非 Null 的值。
1. 變數或運算式已在取值 (Dereference) 之前針對 Null 進行檢查。

當您取消引用在空警告上下文中**可能為空**的變數或表達式時,編譯器將生成警告。 此外,當不可取消的引用類型分配給啟用的空註釋上下文中**的可能為空**變數或表達式時,編譯器將生成警告。

## <a name="attributes-describe-apis"></a>屬性描述 API

向 API 添加屬性,這些屬性向編譯器提供有關參數或返回值何時可以或不能為空的詳細資訊。 您可以在涵蓋[可撤銷屬性](language-reference/attributes/nullable-analysis.md)的語言參考文章中瞭解有關這些屬性的更多內容。 在當前版本和即將發佈的版本中,這些屬性將添加到 .NET 庫中。 首先更新最常用的 API。

## <a name="see-also"></a>另請參閱

- [草稿空參考類型規範](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md)
- [可為 Null 參考教學課程簡介](tutorials/nullable-reference-types.md)
- [將現有的程式碼基底遷移至可為 Null 參考](tutorials/upgrade-to-nullable-references.md)
