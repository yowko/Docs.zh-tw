---
title: "運算式樹狀架構摘要"
description: "概述如何使用運算式樹狀架構來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 8088ce0c138cdb05a6e4a4fb6467e43efd252ba7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees-summary"></a>運算式樹狀架構摘要

[上一個主題 -- 轉譯運算式](expression-trees-translating.md)

在本系列中，您已了解如何使用「運算式樹狀架構」來建立動態程式，將程式碼解譯為資料，並建立以該程式碼為基礎的新功能。

您可以查看運算式樹狀架構，以了解演算法的意圖。 不只是查看該程式碼。 您可以建立表示原始程式碼修改版本的新運算式樹狀架構。

您也可以使用運算式樹狀架構來檢視演算法，並將該演算法轉譯至其他語言或環境。 

## <a name="limitations"></a>限制

某些較新的 C# 語言項目無法正確轉譯為運算式樹狀架構。 運算式樹狀架構不能含有 `await` 運算式或 `async` Lambda 運算式。 C# 6 版本中新增的許多功能，似乎與寫入運算式樹狀架構的功能不同。 相反地，較新的功能會以舊版的對等語法顯示於運算式樹狀架構中。 這可能不如您認為的是項限制。 事實上，這表示當引進新的語言功能時，解譯運算式樹狀架構的程式碼仍可能以相同方式運作。

即使有這些限制，運算式樹狀架構還是可讓您建立與解譯和修改程式碼 (以資料結構表示) 有關的動態演算法。 這是功能強大的工具，而且是 .NET 生態系統的其中一項功能，可讓 Entity Framework 等豐富的程式庫完成其功能。

