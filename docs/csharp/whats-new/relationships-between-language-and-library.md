---
title: "語言功能和程式庫類型之間的關聯性 | Microsoft Docs"
description: "語言功能經常會依賴程式庫類型進行實作。 了解該關聯性。"
keywords: "C# 語言設計，標準程式庫"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: b7de4fdb4356e8822dba6aaaf67d615980ff09cd
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="relationships-between-language-features-and-library-types"></a>語言功能和程式庫類型之間的關聯性

C# 語言定義要求標準程式庫具有特定類型和這些類型的特定可存取成員。 編譯器產生的程式碼會將這些必要的類型和成員用在許多不同的語言功能。 必要時，為尚未部署這些類型或成員的環境撰寫程式碼時，會有包含較新語言版本所需類型的 NuGet 套件。

這種對標準程式庫功能的相依性，自其第一版本開始已成為 C# 語言的一部分。 該版本包含的範例如下：

* <xref:System.Exception> - 用於所有編譯器產生的例外狀況。
* <xref:System.String> - C# `string` 類型是 <xref:System.String> 的同義字。
* <xref:System.Int32> - `int` 的同義字。

第一個版本很簡單：編譯器和標準程式庫一起出貨，各只有一個版本。

後續的 C# 版本偶爾會在相依性中新增新的類型或成員。 範例包括 <xref:System.Runtime.CompilerServices.INotifyCompletion>、<xref:System.Runtime.CompilerServices.CallerFilePathAttribute> 和 <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>。 C# 7.0 會繼續此行為，在 <xref:System.ValueTuple> 新增相依性實作 [Tuple](../tuples.md) 語言功能。

語言設計小組努力將相容標準程式庫中所需類型和成員的介面區縮減至最小。 該目標與新程式庫功能順利併入到語言的全新設計平衡。 未來的 C# 版本中會有在標準程式庫中需要新類型和成員的新功能。 請務必了解如何管理工作中的這些相依性。

## <a name="managing-your-dependencies"></a>管理相依性

C# 編譯器工具現在已從受支援平台上的 .NET 程式庫發行週期中分離出來。 事實上，不同的 .NET 程式庫有不同的發行週期：Windows 上的 .NET Framework 發行為 Windows Update，.NET Core 隨附於個別的排程，而 Xamarin 版的程式庫更新則隨每個目標平台的 Xamarin 工具出貨。

大多時候您都不會注意到這些變更。 不過，當您使用較新的語言版本，需要該平台 .NET 程式庫尚未提供的功能時，要參考 NuGet 套件以提供這些新的類型。
使用新的 Framework 安裝更新您的應用程式支援平台時，您可以移除額外的參考。

這項分隔表示，即使您的目標機器可能沒有對應的架構，您仍可以使用新的語言功能。
