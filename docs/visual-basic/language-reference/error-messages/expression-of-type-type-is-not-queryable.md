---
title: 類型 <type> 的運算式無法查詢
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: d605243c213166f20592fdc440a3362f957ebbf2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163060"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a>BC36593：類型的運算式不可 \<type> 查詢

型別的運算式 \<type> 無法查詢。 請確定您沒有遺漏元件參考及（或） LINQ 提供者的命名空間匯入。

 可查詢的類型定義于 <xref:System.Linq> 、 <xref:System.Data.Linq> 和 <xref:System.Xml.Linq> 命名空間中。 您必須匯入一或多個這些命名空間，才能執行 LINQ 查詢。

 <xref:System.Linq>命名空間可讓您使用 LINQ 查詢物件，例如集合和陣列。

 <xref:System.Data.Linq>命名空間可讓您使用 LINQ 查詢 ADO.NET 資料集和 SQL Server 資料庫。

 <xref:System.Xml.Linq>命名空間可讓您使用 LINQ 查詢 xml，並在 Visual Basic 中使用 xml 功能。

 **錯誤識別碼：** BC36593

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 將 `Import` <xref:System.Linq> 、 <xref:System.Data.Linq> 或命名空間的語句新增 <xref:System.Xml.Linq> 至程式碼檔案。 您也可以使用 [專案設計工具] 的 [ **參考** ] 頁面 ([我的 **專案** ]) 來匯入專案的命名空間。

2. 確定您已識別為查詢來源的類型是可查詢的類型。 也就是實作為或的型別 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> 。

## <a name="see-also"></a>另請參閱

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [Visual Basic 中的 LINQ 簡介](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../programming-guide/language-features/linq/index.md)
- [XML](../../programming-guide/language-features/xml/index.md)
- [References 與 Imports 陳述式](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../statements/imports-statement-net-namespace-and-type.md)
- [專案設計工具，參考頁 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
