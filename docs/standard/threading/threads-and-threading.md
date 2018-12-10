---
title: 執行緒與執行緒處理
ms.date: 11/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET]
- threading [.NET], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 095bd92921c9cd54d3a7d97ed07b35526b85c57f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147673"
---
# <a name="threads-and-threading"></a>執行緒與執行緒處理

多執行緒處理可讓您提高應用程式的回應能力，如果應用程式在多處理器或多核心系統上執行，也可提高其輸送量。

## <a name="processes-and-threads"></a>處理序和執行緒

「處理序」是正在執行的程式。 作業系統使用處理序來分隔正在執行的應用程式。 「執行緒」是要作業系統配置處理器時間的基本單位。 每個執行緒都有[排程優先順序](scheduling-threads.md)，並保有系統在執行緒執行暫停時用來儲存執行緒內容的一組結構。 執行緒內容包括執行緒順暢繼續執行所需的所有資訊，包括執行緒的一組 CPU 暫存器和堆疊。 多個執行緒可在一個處理序中執行。 一個處理序的所有執行緒都共用該處理序的虛擬位址空間。 執行緒可以執行任一部分的程式碼，包括另一個執行緒目前正在執行的部分。

> [!NOTE]
> .NET Framework 提供使用「應用程式定義域」來隔離處理序內應用程式的方式  (應用程式定義域不適用於 .NET Core)。如需詳細資訊，請參閱[應用程式定義域](../../framework/app-domains/application-domains.md)一文的[ 應用程式定義域和執行緒](../../framework/app-domains/application-domains.md#application-domains-and-threads)一節。

根據預設，.NET 程式會從單一執行緒開始，通常稱為「主」執行緒。 不過，它可以建立額外的執行緒與主執行緒平行或同時執行程式碼。 這些執行緒通常稱為「背景工作執行緒」。

## <a name="when-to-use-multiple-threads"></a>使用多執行緒的時機

多執行緒可讓您用來提高應用程式的回應能力，並利用多處理器或多核心系統來提高應用程式的輸送量。

請想一想傳統型應用程式，主執行緒負責處理使用者介面項目和回應使用者動作。 背景工作執行緒可用來執行耗時的作業，否則這些作業會佔用主執行緒，而導致使用者介面沒有回應。 您也可以使用專用執行緒進行網路或裝置的通訊，以更快速地回應內送訊息或事件。

如果您的程式執行可平行完成的作業，那麼在個別執行緒中執行這些作業，並在多處理器或多核心系統上執行程式可減少總執行時間。 在這類系統上，使用多執行緒處理可提高輸送量及回應能力。

## <a name="how-to-use-multithreading-in-net"></a>如何在 .NET 中使用多執行緒處理。

從 .NET Framework 4 開始，建議使用[工作平行程式庫 (TPL)](../parallel-programming/task-parallel-library-tpl.md) 和[平行 LINQ (PLINQ)](../parallel-programming/parallel-linq-plinq.md) 來利用多執行緒處理。 如需詳細資訊，請參閱[平行程式設計](../parallel-programming/index.md)。

TPL 和 PLINQ 都憑藉 <xref:System.Threading.ThreadPool> 執行緒來運作。 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類別會為 .NET 應用程式提供背景工作執行緒集區。 您也可以使用執行緒集區執行緒。 如需詳細資訊，請參閱[受控執行緒集區](the-managed-thread-pool.md)。

最後，您可以使用 <xref:System.Threading.Thread?displayProperty=nameWithType> 代表受控執行緒的類別。 如需詳細資訊，請參閱[使用執行緒和執行緒處理](using-threads-and-threading.md)。

多個執行緒可能需要存取共用資源。 為了讓資源保持在未損毀的狀態並避免競爭條件，您必須同步對該資源的執行緒存取。 您也可能想要協調多個執行緒的互動。 .NET 提供可用來同步對共用資源的存取或協調執行緒互動的一系列類型。 如需詳細資訊，請參閱[同步處理原始物件概觀](overview-of-synchronization-primitives.md)。

請務必處理執行緒中的例外狀況。 執行緒中未處理的例外狀況一般會終止處理序。 如需詳細資訊，請參閱[受控執行緒中的例外狀況](exceptions-in-managed-threads.md)。

## <a name="see-also"></a>另請參閱

- [執行緒物件和功能](threading-objects-and-features.md)
- [受控執行緒處理最佳做法](managed-threading-best-practices.md)
- [.NET 中的平行處理、並行和非同步程式設計](../parallel-processing-and-concurrency.md)
- [About Processes and Threads](/windows/desktop/procthread/about-processes-and-threads) (處理序和執行緒的簡介)