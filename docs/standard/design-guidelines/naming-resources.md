---
title: 命名資源
description: 請參閱 .NET 中資源的命名方針，這類似于命名屬性的指導方針。
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
ms.openlocfilehash: 765337bcf9fad4f9a8c9272a15b5c77d02770471
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768244"
---
# <a name="naming-resources"></a>命名資源
因為可當地語系化的資源可以透過特定物件來參考，如同它們是屬性一樣，資源的命名指導方針類似于屬性方針。

 ✔️在資源金鑰中使用 PascalCasing。

 ✔️提供描述性，而不是簡短識別碼。

 ❌請勿使用主要 CLR 語言的特定語言關鍵字。

 ✔️只在命名資源中使用英數位元和底線。

 ✔️針對例外狀況訊息資源，請使用下列命名慣例。

 資源識別碼應該是例外狀況類型名稱加上例外狀況的簡短識別碼：

 `ArgumentExceptionIllegalCharacters` `ArgumentExceptionInvalidName`
 `ArgumentExceptionFileNameIsMalformed`

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [命名方針](naming-guidelines.md)
