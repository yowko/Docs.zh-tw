---
title: .NET 規則運算式中的字元逸出
description: 了解 .NET 規則運算式中的特殊字元和逸出字元。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET Framework regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
author: rpetrusha
ms.author: ronpet
ms.custom: seodec18
ms.openlocfilehash: 248d434f7aad56d84d952fa27cf49f3d370f4a1c
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "69934836"
---
# <a name="character-escapes-in-regular-expressions"></a>在規則運算式中執行字元逸出
規則運算式中的反斜線 (\\) 表示下列其中之一：  
  
- 它後面所接的字元是特殊字元，如下節中的資料表所示。 比方說，`\b` 是表示規則運算式比對應該在文字邊界上開始的一個錨點，`\t` 代表索引標籤，而 `\x020` 代表空間。  
  
- 一個字元應該依其字面來解譯，否則會被解譯為未逸出的語言結構。 例如，括號 (`{`) 開始定義數量詞，但是反斜線後面接著一個括號 (`\{`) 則表示規則運算式引擎應該與括號相符。 同樣地，單一反斜線標記逸出的語言建構之開頭，但兩個反斜線 (`\\`) 表示規則運算式引擎應該符合反斜線。  
  
> [!NOTE]
> 逸出字元會在規則運算式模式而不是在取代模式中被辨識。  
  
## <a name="character-escapes-in-net"></a>.NET 中的逸出字元  
 下表列出 .NET 中的規則運算式所支援的逸出字元。  
  
|字元或序列|描述|  
|---------------------------|-----------------|  
|下列字元以外的所有字元：<br /><br /> . $ ^ { [ ( &#124; ) * + ? \ |不同於列在 [字元或序列] 資料行中的其他字元在規則運算式中沒有任何特殊的意義；它們符合其本身。<br /><br /> [字元或序列] 資料行中所包含的字元是規則運算式的特殊語言項目。 若要在規則運算式中進行比對，它們必須逸出或包含在[正字元群組](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。 例如，規則運算式 `\$\d+` 或 `[$]\d+` 符合「$1200」。|  
|`\a`|符合警鈴 (警示) 字元 `\u0007`。|  
|`\b`|在 `[`*character_group*`]` 字元類別，比對退格鍵 `\u0008`。  (請參閱[字元類別](../../../docs/standard/base-types/character-classes-in-regular-expressions.md)。)在字元類別之外， `\b` 符合文字邊界錨點。 (請參閱[錨點](../../../docs/standard/base-types/anchors-in-regular-expressions.md)。)|  
|`\t`|符合索引標籤， `\u0009`。|  
|`\r`|符合歸位字元， `\u000D`。 請注意，`\r` 不等於新行字元 `\n`。|  
|`\v`|符合垂直定位， `\u000B`。|  
|`\f`|符合換頁字元， `\u000C`。|  
|`\n`|符合新行字元， `\u000A`。|  
|`\e`|符合逸出字元， `\u001B`。|  
|`\` *nnn*|符合 ASCII 字元，其中 *nnn* 是由代表八進位字元碼的兩個或三個數字所組成。 例如，`\040` 代表空格字元。 其若只有一個數字 (例如 `\2`)，或其對應至擷取群組的編號，會將此建構解譯為反向參考 (請參閱[反向參考建構](../../../docs/standard/base-types/backreference-constructs-in-regular-expressions.md)。)|  
|`\x` *nn*|符合 ASCII 字元，其中 *nn* 是兩位數的十六進位字元碼。|  
|`\c` *X*|符合 ASCII 控制字元，其中 X 是控制字元的字母。 例如，`\cC` 是 CTRL + C。|  
|`\u` *nnnn*|符合 UTF-16 字碼單位，其值為十六進位的 *nnnn*。 **注意：** .NET 不支援用來指定 Unicode 的 Perl 5 逸出字元。 Perl 5 字元逸出的形式是 `\x{` *####* `…}`，其中 *####* `…` 是一系列的十六進位數字。 請改用 `\u`*nnnn*。|  
|`\`|當後面加上一個不被認為是逸出的字元時，符合該字元。 例如，`\*` 符合使用星號 (*)，而且與 `\x2A` 相同。|  
  
## <a name="an-example"></a>範例  
 下列範例說明如何在規則運算式中使用逸出字元。 它會剖析字串，包含在 2009 年世界上最大城市的名稱以及人口。 每個城市名稱及其人口數目被 Tab (`\t`) 或分隔號 (&#124; 或 `\u007c`) 分開。 個別的城市及其人口是被歸位字元和換行字元分隔開的。  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 規則運算式 `\G(.+)[\t|\u007c](.+)\r?\n` 的解譯方式如下表所示。  
  
|模式|描述|  
|-------------|-----------------|  
|`\G`|從最後比對結束之處開始比對。|  
|`(.+)`|一或多次比對任何字元。 這是第一個擷取群組。|  
|`[\t\u007c]`|比對 Tab (`\t`) 或分隔號 (&#124;)。|  
|`(.+)`|一或多次比對任何字元。 這是第二個擷取群組。|  
|`\r?\n`|比對後面接著新行的歸位字元其中的零或指定項目。|  
  
## <a name="see-also"></a>另請參閱

- [規則運算式語言 - 快速參考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
