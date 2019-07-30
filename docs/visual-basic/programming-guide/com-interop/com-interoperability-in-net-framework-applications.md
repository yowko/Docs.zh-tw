---
title: .NET Framework 應用程式中的 COM 互通性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: 758f065d2e0e7f8200529ef171dc89f94950b46e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627085"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework 應用程式中的 COM 互通性 (Visual Basic)

當您想要在相同的應用程式中使用 COM 物件和 .NET Framework 物件時, 您必須解決物件存在於記憶體中的差異。 .NET Framework 物件位於 managed 記憶體中 (由 common language runtime 所控制的記憶體), 而且可以視需要由執行時間移動。 COM 物件位於非受控記憶體中, 因此不應該移至另一個記憶體位置。 Visual Studio 和 .NET Framework 提供工具來控制這些受控和非受控元件的互動。 如需 managed 程式碼的詳細資訊, 請參閱[Common Language Runtime](../../../standard/clr.md)。

除了在 .NET 應用程式中使用 COM 物件, 您可能也會想要使用 Visual Basic 來開發可透過 COM 從非受控程式碼存取的物件。

此頁面上的連結提供 COM 和 .NET Framework 物件之間互動的詳細資料。

## <a name="related-sections"></a>相關章節

| | |
|---------|---------|
| [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md) | 提供涵蓋 Visual Basic 中 COM 互通性主題的連結, 包括 COM 物件、ActiveX 控制項、Win32 Dll、managed 物件, 以及 COM 物件的繼承。 |
| [與 Unmanaged 程式碼互通](../../../framework/interop/index.md) | 簡短描述 managed 和非受控碼之間的一些互動問題, 並提供進一步研究的連結。 |
| [COM 包裝函式](../../../standard/native-interop/com-wrappers.md) | 討論執行時間可呼叫包裝函式, 其可讓 managed 程式碼呼叫 COM 方法和 COM 可呼叫包裝函式, 以允許 COM 用戶端呼叫 .NET 物件方法。 |
| [進階 COM 互通性](../../../framework/interop/index.md) | 提供主題連結, 其中包含與包裝函式、例外狀況、繼承、執行緒、事件、轉換和封送處理相關的 COM 互通性。 |
| [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md) | 討論您可以用來將 COM 類型程式庫中找到的類型定義轉換成 common language runtime 元件中的對等定義的工具。 |
