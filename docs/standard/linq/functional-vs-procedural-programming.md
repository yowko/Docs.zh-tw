---
title: 功能性與程式性程式設計
description: LINQ to XML 支援功能結構和程式技術來建立 XML 應用程式。 功能結構是宣告式的方法。 程式技術支援 XML 樹狀結構的記憶體內部修改。
ms.date: 07/20/2015
ms.assetid: fc64e39c-a487-4882-9169-da4de97917d9
ms.openlocfilehash: a2753a31e88fd338dad61063f559431869b9e17f
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552131"
---
# <a name="functional-vs-procedural-programming-linq-to-xml"></a>功能性與程式設計 (LINQ to XML) 

XML 應用程式有很多種：

- 有些應用程式會採用 XML 來源文件，然後以不同於來源文件的組織結構產生新的 XML 文件。
- 有些應用程式會採用 XML 來源文件，然後以完全不同的形式 (例如，HTML 或 CSV 文字檔)，產生結果文件。
- 有些應用程式會採用 XML 來源文件，然後將記錄插入到資料庫中。
- 有些應用程式會從其他來源 (例如，資料庫) 取得資料，然後從其中建立 XML 文件。

這些都不是 XML 應用程式的所有類型，但這些都是 XML 程式設計人員必須執行的一組具代表性的功能。

利用所有這些應用程式類型，開發人員可以採用兩種明顯不同的方法：

- 使用宣告式方法的功能結構。
- 使用程序性程式碼進行記憶體中 XML 樹狀結構修改。

LINQ to XML 同時支援這兩種方法。

使用功能性方法時，您可以撰寫採用來源文件的轉換，然後利用所需的組織結構產生全新的結果文件。

就地修改 XML 樹狀結構時，您可以撰寫可在記憶體中 XML 樹狀結構內周遊與導覽程式碼的程式碼，藉以在必要時插入、刪除與修改程式碼。

您可以搭配任一種方法使用 LINQ to XML。 您可以使用相同的類別，在某些情況下，也可以使用相同的方法。 不過，這兩種方法的結構和目標並不相同。 例如，在不同的情況下，其中一種方法的效能通常會比較好，而且或多或少會使用到記憶體。 此外，其中一種方法會比較容易撰寫，並產生較容易維護的程式碼。

若要查看這兩種方法的對比，請參閱 [記憶體中的 XML 樹狀結構修改與功能結構](in-memory-xml-tree-modification-vs-functional-construction.md)。

如需撰寫功能性轉換的教學課程，請參閱 [純功能性轉換簡介](introduction-pure-functional-transformations.md)。
