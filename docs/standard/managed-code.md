---
title: "什麼是 Managed 程式碼？"
description: "了解 Managed 程式碼的撰寫方式，其執行是由執行階段 Common Language Runtime (CLR) 所管理。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.translationtype: HT
ms.sourcegitcommit: 3155295489e1188640dae5aa5bf9fdceb7480ed6
ms.openlocfilehash: 263662c1c7f22c84e0de14c6480fa9807b46b2f2
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---

# <a name="what-is-managed-code"></a>什麼是 Managed 程式碼？

使用 .NET Framework 時，您經常會遇到「Managed 程式碼」一詞。 本文件將說明此詞彙所代表的意義及其他相關資訊。

簡單來說，Managed 程式碼就是其執行受到執行階段管理的程式碼。 在此情況下，不論實作為何 ([Mono](http://www.mono-project.com/)、.NET Framework 或 .NET Core)，所提到的執行階段都稱為 **Common Language Runtime** 或 CLR。 CLR 負責將 Managed 程式碼編譯成機器碼，再加以執行。 此外，執行階段提供幾項重要服務，例如自動記憶體管理、安全性界限、型別安全等。

與此相反的是您執行 C/C++ 程式的方式，又稱為「Unmanaged 程式碼」。 在 Unmanaged 世界中，程式設計人員會負責處理幾乎所有工作。 實際程式基本上是作業系統 (OS) 載入記憶體並啟動的二進位檔。 從記憶體管理到安全性考量等其他工作都是程式設計人員的責任。

Managed 程式碼是以其中一種高階語言撰寫而成 (例如 C#、Visual Basic、F# 等)，並可在 .NET 上執行。 當您使用這些語言各自的編譯器來編譯以這些語言撰寫的程式碼時，您不會取得機器碼。 您會取得稍後可供執行階段編譯及執行的**中繼語言**碼。 這項規則的唯一例外是 C++，因為它也會產生在 Windows 上執行的原生、Unmanaged 二進位檔。

## <a name="intermediate-language--execution"></a>中繼語言和執行

什麼是「中繼語言」(簡稱 IL)？ 它是以高階 .NET 語言撰寫之程式碼的編譯結果。 當您編譯以其中一種語言撰寫的程式碼之後，您會取得由 IL 所組成的二進位檔。 請務必注意，IL 與在執行階段上執行的任何特定語言都無關；它甚至有個別的規格，如果您想要，可以閱讀此規格。

當您從高階程式碼產生 IL 之後，您可能想要執行它。 此時 CLR 會接管，並開始 **Just-In-Time** 編譯 (或 **JIT-ing**) 的程序，以將您的程式碼從 IL 編譯成可實際在 CPU 上執行的機器碼。 如此一來，CLR 就會知道您程式碼的實際功能，並可有效地進行「管理」。

中繼語言有時也稱為通用中間語言 (CIL) 或 Microsoft Intermediate Language (MSIL)。

## <a name="unmanaged-code-interoperability"></a>Unmanaged 程式碼互通性

當然，CLR 允許超過 Managed 與 Unmanaged 世界之間的界限，而且有許多程式碼會這樣做，甚至是在[基底類別庫](framework-libraries.md)中。 這稱為**互通性** 或簡稱 **Interop**。 這些佈建可讓您包裝並呼叫 Unmanaged 程式庫。 不過，請務必請注意，一旦您這樣做，當程式碼超過執行階段的界限時，執行的實際管理會再次交由 Unmanaged 程式碼，因此會受到相同的限制。

同樣地，C# 語言可讓您在程式碼中直接使用 Unmanaged 建構 (例如資料指標)，方法是利用所謂的 **unsafe 內容**，來指定程式碼片段的執行不受 CLR 管理。

## <a name="more-resources"></a>更多資源

*   [.NET Framework 的概觀](https://msdn.microsoft.com/library/zw4w595w.aspx)
*   [Unsafe 程式碼和指標](https://msdn.microsoft.com/library/t2yzs44b.aspx)
*   [互通性 (C# 程式設計手冊)](https://msdn.microsoft.com/library/ms173184.aspx)

