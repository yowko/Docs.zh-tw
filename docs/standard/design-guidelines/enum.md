---
title: 列舉設計
description: 列舉的設計，這是一種特殊的實值型別。 簡單列舉會保存小型的封閉選項組。 旗標列舉支援列舉值的位運算。
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: a2e19197b114daa2a0956a6fc87231a6a81de916
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821355"
---
# <a name="enum-design"></a>列舉設計

列舉是一種特殊類型的實值型別。 列舉有兩種：簡單列舉和旗標列舉。

簡單列舉代表小型封閉的選項組。 簡單列舉的常見範例是一組色彩。

旗標列舉是設計用來支援列舉值的位運算。 旗標列舉的常見範例是選項清單。

✔️請使用列舉來表示值集合的強型別參數、屬性和傳回值。

✔️會偏好使用列舉，而不是靜態常數。

❌ 請勿將列舉用於開放集 (例如作業系統版本、朋友名稱等 ) 。

❌ 請勿提供預定的列舉值供日後使用。

您一律可以在稍後的階段中，直接將值加入至現有的列舉。 如需將值加入至列舉的詳細資訊，請參閱 [將值加入至](#add_value) 列舉。 保留值只是會污染實際值的集合，而且通常會導致使用者錯誤。

❌ 避免公開只具有一個值的列舉。

確保 C Api 未來擴充性的常見做法是將保留參數新增至方法簽章。 這類保留的參數可表示為具有單一預設值的列舉。 這不應該在受控 Api 中完成。 方法多載可讓您在未來的版本中加入參數。

❌ 請勿將 sentinel 值包含在列舉中。

雖然它們有時對架構開發人員很有説明，但 sentinel 值對架構的使用者感到混淆。 它們可用來追蹤列舉的狀態，而不是列舉所表示之集合中的其中一個值。

✔️在簡單列舉上提供值為零。

請考慮呼叫值，例如「無」。 如果這類的值不適用於此特定列舉，則列舉的最常見預設值應指派為零的基礎值。

✔️考慮使用 <xref:System.Int32> (大部分程式設計語言中的預設值，) 作為列舉的基礎類型，除非下列任何條件成立：

- 列舉是旗標列舉，而您有超過32個旗標，或預期未來會有更多的旗標。

- 基礎類型必須不同于 <xref:System.Int32> ，以便與非受控程式碼的互通性需要不同大小的列舉。

- 較小的基礎類型會大幅節省空間。 如果您預期列舉主要是用來做為控制流程的引數，則大小會有很大的差異。 如果有下列情況，節省的大小可能很大：

  - 您預期列舉是用來做為極常具現化之結構或類別中的欄位。

  - 您希望使用者能夠建立大型陣列或列舉實例的集合。

  - 您預期要序列化的列舉實例數量很多。

針對記憶體中的使用方式，請注意，managed 物件永遠保持 `DWORD` 一致，因此，您實際上需要在實例中使用多個列舉或其他小型結構來封裝較小的列舉，以使其成為差異，因為實例大小總計一律會無條件進位至 `DWORD` 。

✔️使用複數名詞或名詞片語，以及具有單數名詞或名詞片語的簡單列舉進行名稱旗標列舉。

❌ 請勿直接延伸 <xref:System.Enum?displayProperty=nameWithType> 。

<xref:System.Enum?displayProperty=nameWithType> 這是 CLR 用來建立使用者定義列舉的特殊類型。 大部分的程式設計語言都會提供程式設計項目，讓您能夠存取這項功能。 例如，在 c # 中， `enum` 關鍵字是用來定義列舉。

<a name="design"></a>

### <a name="designing-flag-enums"></a>設計旗標列舉

✔️將套用 <xref:System.FlagsAttribute?displayProperty=nameWithType> 至旗標列舉。 請勿將此屬性套用至簡單列舉。

✔️會使用兩個旗標列舉值的乘冪，以便使用位 OR 運算自由地結合。

✔️考慮為常用的旗標組合提供特殊的列舉值。

位運算是先進的概念，簡單的工作則不需要。 <xref:System.IO.FileAccess.ReadWrite> 這是這類特殊值的範例。

❌ 避免建立旗標列舉，其中某些值的組合無效。

❌ 請避免使用旗標列舉值零，除非此值代表「所有旗標已清除」，並且依照下一個指導方針的規定適當命名。

✔️請將旗標列舉的值命名為零 `None` 。 針對旗標列舉，此值必須一律表示「所有旗標已清除」。

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a>將值新增至列舉

很常見的情況是，您必須在將值傳送至列舉之後，將其加入至列舉。 從現有的 API 傳回新加入的值時，可能會發生應用程式相容性問題，因為寫入不良的應用程式可能無法正確地處理新值。

✔️考慮將值新增至列舉（儘管有較小的相容性風險）。

如果您有關于新增至列舉的應用程式不相容的實際資料，請考慮加入新的 API，以傳回新的和舊的值，並取代舊的 API，這應該只會繼續傳回舊的值。 這可確保您現有的應用程式保持相容。

*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)
