---
title: .NET Framework 應用程式中的 COM 互通性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 6e8b4eba40cc1872cb289ca120679bb951f2652a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920801"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework 應用程式中的 COM 互通性 (Visual Basic)

當您想要在相同的應用程式中使用 COM 物件和.NET Framework 物件時，您需要解決的物件存在於記憶體中的差異。 .NET Framework 物件位於 managed 記憶體 — common language runtime 所控制的記憶體，並可以由執行階段移動，視需要。 COM 物件位在 unmanaged 記憶體，且不應該將移至另一個記憶體位置。 Visual Studio 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。 如需有關 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](../../../standard/clr.md)。

除了.NET 應用程式中使用 COM 物件，您可能也想要使用 Visual Basic 來開發可從 unmanaged 程式碼，透過 COM 存取的物件

此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。

## <a name="related-sections"></a>相關章節

| | |
|---------|---------|
| [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) | 提供連結，這些主題涵蓋在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll，受管理的物件，以及繼承的 COM 物件的 COM 互通性。 |
| [與 Unmanaged 程式碼互通](../../../framework/interop/index.md) | 簡要說明一些 managed 和 unmanaged 程式碼之間的互動問題，並提供進一步的研究的連結。 |
| [COM 包裝函式](../../../framework/interop/com-wrappers.md) | 討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件的方法。 |
| [進階 COM 互通性](../../../framework/interop/index.md) | 提供涵蓋相對於包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換和封送處理 COM 互通性的主題連結。 |
| [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | 討論您可以用來轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。 |