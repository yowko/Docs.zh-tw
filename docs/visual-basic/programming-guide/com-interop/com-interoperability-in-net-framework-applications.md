---
title: ".NET Framework 應用程式 (Visual Basic) 中的 COM 互通性 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 308ee8e495efa9368ef55d781f6b6dc314db51ac
ms.lasthandoff: 03/13/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework 應用程式中的 COM 互通性 (Visual Basic)
當您想要在相同的應用程式中使用 COM 物件和.NET Framework 物件時，您需要處理的物件存在於記憶體中的差異。 在.NET Framework 物件位於 managed 記憶體 — common language runtime 所控制的記憶體，視需要可由執行階段移。 COM 物件位於 unmanaged 記憶體中，而且不應該將移至另一個記憶體位置。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]而[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]提供工具來控制這些互動 managed 和 unmanaged 元件。 如需 managed 程式碼的詳細資訊，請參閱[Common Language Runtime](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)。  
  
 除了.NET 應用程式中使用 COM 物件，您可能也想要使用[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]來開發可從 unmanaged 程式碼，透過 COM 存取的物件  
  
 此頁面上的連結提供 COM 和.NET Framework 物件之間的互動的詳細資料。  
  
## <a name="related-sections"></a>相關章節  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 提供連結，這些主題涵蓋在 Visual Basic 中，包括 COM 物件、 ActiveX 控制項、 Win32 Dll、 受管理的物件和 COM 物件的繼承的 COM 互通性。  
  
 [COM Interop 包裝函式錯誤](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 專案系統無法建立特定元件的 COM 互通性包裝函式所描述的後果和選項。  
  
 [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/sd10k43k)  
 簡短描述 managed 和 unmanaged 程式碼之間的互動問題，並提供連結，如需進一步的研究。  
  
 [COM 包裝函式](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 討論執行階段可呼叫包裝函式，可讓 managed 程式碼呼叫 COM 方法，以及 COM 可呼叫包裝函式，可讓 COM 用戶端呼叫.NET 物件的方法。  
  
 [進階的 COM 互通性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 提供連結，這些主題涵蓋與包裝函式、 例外狀況、 繼承、 執行緒、 事件、 轉換、 轉換和封送處理 COM 互通性。  
  
 [Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 討論您可以使用轉換為通用語言執行階段組件中的等效定義 COM 類型程式庫中找到的類型定義的工具。
