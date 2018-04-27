---
title: -具決定性
ms.date: 04/11/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
- -deterministic compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 273abf8811f04cd7f58599ce3421ca1f17c740d9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="-deterministic"></a>-具決定性

可讓編譯器產生其位元組的輸出編譯針對相同的輸入是相同的組件。 

## <a name="syntax"></a>語法

```
-deterministic
```

## <a name="remarks"></a>備註

根據預設，編譯器輸出一組給定的輸入是唯一的因為編譯器會加入時間戳記和 GUID 產生的隨機數字。 您使用`-deterministic`選項來產生*具決定性的組件*，其二進位內容是相同跨編譯，只要輸入維持不變。

編譯器會考慮以決定性的下列輸入：

- 命令列參數的順序。
- 編譯器的.rsp 回應檔案的內容。
- 精確的編譯器版本使用，以及其參考組件。
- 目前的目錄路徑。
- 所有檔案的二進位內容明確地傳遞給編譯器以直接或間接方式包括： 
    - 原始程式檔
    - 參考的組件
    - 參考的模組
    - 資源
    - 強式名稱金鑰檔
    - @ 回應檔
    - 分析器
    - Ruleset
    - 其他可能被分析器用的檔案
- （適用於診斷和例外狀況訊息所產生的語言） 目前的文化特性。
- 預設編碼方式 （或目前的字碼頁） 如果未指定編碼方式。
- 是否存在、 不存在，並在編譯器搜尋路徑上檔案的內容 (例如，所指定`/lib`或`/recurse`)。
- CLR 平台編譯器會在其執行。
- 值`%LIBPATH%`，而影響分析器相依性的載入。

來源可公開可用時，具決定性的編譯可以用於建立是否來自信任來源編譯二進位檔。 它也可用於連續的建置系統，以判斷是否需要執行建置步驟會取決於二進位檔的變更。 

## <a name="see-also"></a>另請參閱
[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
[編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
