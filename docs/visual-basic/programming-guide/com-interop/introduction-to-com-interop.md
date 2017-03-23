---
title: "COM Interop (Visual Basic) 簡介 |Microsoft 文件"
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
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
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
ms.openlocfilehash: 8866dbadca040c57ed2b59540dd2c341eb81758c
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Interop 簡介 (Visual Basic)
元件物件模型 (COM) 可讓您公開其功能給其他元件和主應用程式的物件。 雖然已 Windows 程式設計多年的基礎 COM 物件，如 common language runtime (CLR) 所設計的應用程式有許多好處。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式最終會取代開發的 com。 在那之前，您可能要使用或建立 COM 物件使用[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。 與 COM 互通性或*COM interop*，可讓您使用現有的 COM 物件時，轉換到[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]您自己的步調。  
  
 使用[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]建立 COM 元件，您可以使用免註冊 COM interop。 這可讓您控制當多個版本的電腦上，安裝並可讓使用者可以使用 XCOPY 或 FTP 將您的電腦上的適當目錄的應用程式可以執行它要啟用哪個 DLL 版本。 如需詳細資訊，請參閱[免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)。  
  
## <a name="managed-code-and-data"></a>Managed 程式碼和資料  
 程式碼開發的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]稱為*managed 程式碼*，並包含可由 CLR 的中繼資料。 所使用的資料[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式會呼叫*管理資料*因為執行階段會管理資料相關工作，例如配置與回收記憶體，以及執行型別檢查。 根據預設，[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]使用 managed 程式碼和資料，但您可以存取 unmanaged 程式碼和資料的 COM 物件使用 interop 組件 （在此頁面稍後說明）。  
  
## <a name="assemblies"></a>組件  
 組件是主要建置組塊的[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。 它是功能，可建置、 版本控制，以及部署為包含一或多個檔案的單一實作單元的集合。 每個組件包含組件資訊清單。  
  
## <a name="type-libraries-and-assembly-manifests"></a>型別程式庫和組件資訊清單  
 型別程式庫描述 COM 物件，例如成員名稱和資料類型的特性。 組件資訊清單執行相同的功能，如[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。 包括下列資訊︰  
  
-   組件識別、 版本、 文化特性和數位簽章。  
  
-   構成組件實作的檔案。  
  
-   型別和構成組件的資源。 這包括從其匯出。  
  
-   對其他組件的編譯時間相依性。  
  
-   組件正確執行所需的權限。  
  
 如需組件和組件資訊清單的詳細資訊，請參閱[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)。  
  
### <a name="importing-and-exporting-type-libraries"></a>匯入和匯出類型程式庫  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]包含公用程式，可讓您從類型程式庫匯入資訊的 Tlbimp[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式。 您可以使用 Tlbexp 公用程式，從組件產生型別程式庫。  
  
 Tlbimp 和 Tlbexp 的相關資訊，請參閱[Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)和[Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 Interop 組件是[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]組件的橋接器之間 managed 和 unmanaged 程式碼，為對等用法的對應 COM 物件成員[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]管理成員。 所建立的 interop 組件[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]處理許多使用 COM 物件，例如交互操作性封送處理的詳細資料。  
  
## <a name="interoperability-marshaling"></a>互通性封送處理  
 所有[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]應用程式都共用一組啟用物件，不論所使用的程式設計語言的互通性的一般型別。 參數和傳回值的 COM 物件有時候會使用 managed 程式碼中使用的不同資料類型。 *互通性封送處理*移動的 COM 物件會封裝參數和傳回值，為對等資料類型的程序。 如需詳細資訊，請參閱[Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)。  
  
## <a name="see-also"></a>另請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)   
 [逐步解說︰ 實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [與 Unmanaged 程式碼互通](https://msdn.microsoft.com/library/sd10k43k)   
 [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [Interop 封送處理](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
