---
title: .NET Framework 應用程式中的 COM 互通性 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25fbde3845d378d4a2bcfc13c71124ad1bc29514
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework 應用程式中的 COM 互通性 (Visual Basic)
當您想要使用相同的應用程式中的 COM 物件和.NET Framework 物件時，您必須先解決物件存在於記憶體中的差異。 .NET Framework 物件位於 managed 記憶體中，控制由 common language runtime 的記憶體，而且可能會視需要移動由執行階段。 COM 物件位於 unmanaged 記憶體中，而且不應該將移到另一個記憶體位置。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。 如需 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](../../../standard/clr.md)。  
  
 除了.NET 應用程式中使用之 COM 物件，您可能也想要使用 Visual Basic 開發可從 unmanaged 程式碼，透過 COM 物件  
  
 在此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。  
  
## <a name="related-sections"></a>相關章節  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 提供包含在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll，受管理的物件，以及繼承的 COM 物件的 COM 互通性主題的連結。  
  
 [COM Interop 包裝函式錯誤](/cpp/misc/com-interop-wrapper-error)  
 描述如果專案系統無法建立特定元件的 COM 互通性包裝函式的結果和選項。  
  
 [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)  
 簡要說明 managed 和 unmanaged 程式碼之間的互動問題，並提供進一步的研究的連結。  
  
 [COM 包裝函式](../../../framework/interop/com-wrappers.md)  
 討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件方法。  
  
 [進階 COM 互通性](../../../framework/interop/index.md)  
 提供包含相對於包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換、 轉換和封送處理的 COM 互通性主題的連結。  
  
 [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 討論可用來將轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。
