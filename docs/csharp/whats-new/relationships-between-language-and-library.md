---
title: "語言功能和程式庫類型之間的關聯性 |Microsoft 文件"
description: "語言功能經常會依賴程式庫類型實作。 了解該關聯性。"
keywords: "C# 語言設計中，標準程式庫"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a>語言功能和程式庫類型之間的關聯性

C# 語言定義需要具有特定型別和特定可存取的成員在這些類型的標準程式庫。 編譯器會產生許多不同的語言功能會使用這些必要的型別和成員的程式碼。 必要時，有包含的類型撰寫程式碼，其中這些型別或成員具有尚未部署的環境時，所需的語言的較新版本的 NuGet 封裝。

這種相依性的標準程式庫功能已自其第一個版本的 C# 語言的一部分。 在該版本中，包含的範例：

* <xref:System.Exception>-用於編譯器產生的所有例外狀況。
* <xref:System.String>-C#`string`類型是同義字<xref:System.String>。
* <xref:System.Int32>-的同義字`int`。

第一個版本很簡單： 編譯器和標準程式庫隨附在一起，而且每個版本，只有一個。

後續版本的 C# 偶爾會有新增新的型別或成員的相依性。 範例包括： <xref:System.Runtime.CompilerServices.INotifyCompletion>，<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>和<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>。 C# 7.0 會繼續這上新增相依性<xref:System.ValueTuple>實作[tuple](../tuples.md)語言功能。

語言設計團隊的運作方式的類型和相容的標準程式庫中所需成員的介面區最小化。 針對全新設計，其中新程式庫功能會併入到語言的順暢地平衡該目標。 會在 C# 需要新類型的未來版本中的新功能和標準程式庫中的成員。 請務必了解如何管理您的工作中的這些相依性。

## <a name="managing-your-dependencies"></a>管理相依性

C# 編譯器工具現在會分開.NET 程式庫支援的平台上的發行週期。 事實上，不同的.NET 程式庫有不同的發行週期： 在 Windows 上的.NET Framework 與 Windows Update relesed，.NET Core 隨附於個別的排程，並利用 Xamarin 工具，為每個目標平台程式庫更新出貨的 Xamarin 版本。

大部分的時間，您可能會發現這些變更。 不過，當您正在該平台上不需要功能的語言，但是.NET 程式庫中的較新版本，將參考的 NuGet 套件，以提供這些新的類型。
為新的 framework 安裝會更新您的應用程式支援的平台，您可以移除額外的參考。

這項分隔表示即使您的目標機器可能無法正確對應的架構，您可以使用新語言功能。
