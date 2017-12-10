---
title: "COM Interop 簡介 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 13df7dc6b325b97411b910c0fc8e05e65a332dc5
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/09/2017
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Interop 簡介 (Visual Basic)
元件物件模型 (COM) 可讓您公開其功能給其他元件和主控件應用程式的物件。 COM 物件已被 Windows 程式設計多年的基礎，而針對 common language runtime (CLR) 所設計的應用程式會提供許多優點。  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式最終會取代開發的 com 之前，您可能要使用或建立 COM 物件使用[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]。 與 COM 互通性或*COM interop*，可讓您使用現有的 COM 物件時轉換為[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]您自己的步調。  
  
 使用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]若要建立 COM 元件，您可以使用免註冊 COM interop。 這可讓您控制的電腦上，安裝一個以上的版本，而且可讓使用者可以使用 XCOPY 或 FTP 將複製到其電腦上的適當目錄的應用程式可以執行它時，系統會啟用 DLL 版本。 如需詳細資訊，請參閱[免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)。  
  
## <a name="managed-code-and-data"></a>Managed 程式碼和資料  
 程式碼開發的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]稱為*managed 程式碼*，且包含可由 CLR 的中繼資料。 所使用的資料[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式會呼叫*受管理的資料*因為執行階段會與資料相關的工作，例如配置和回收記憶體，以及執行類型檢查。 根據預設，Visual Basic.NET 中使用 managed 程式碼和資料，但您可以存取 unmanaged 程式碼和 COM 物件使用 interop 組件 （稍後會說明在此頁面上） 的資料。  
  
## <a name="assemblies"></a>組件  
 組件為主要建置組塊的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 它是功能，可建置、 版本設定，以及部署為包含一或多個檔案的單一實作單元的集合。 每個組件包含組件資訊清單。  
  
## <a name="type-libraries-and-assembly-manifests"></a>類型程式庫和組件資訊清單  
 類型程式庫描述的 COM 物件，例如成員名稱和資料類型的特性。 組件資訊清單執行相同的功能，如[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 包括下列資訊：  
  
-   組件識別、 版本、 文化特性和數位簽章。  
  
-   組成組件實作的檔案。  
  
-   型別和構成組件的資源。 這包括從它匯出。  
  
-   其他組件上的編譯時間相依性。  
  
-   若要正確執行組件所需的權限。  
  
 如需有關組件和組件資訊清單的詳細資訊，請參閱[組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)。  
  
### <a name="importing-and-exporting-type-libraries"></a>匯入和匯出類型程式庫  
 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]包含的公用程式，可讓您從至類型程式庫匯入資訊的 Tlbimp[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 您可以使用 Tlbexp 公用程式，從組件產生類型程式庫。  
  
 如需 Tlbimp 和 Tlbexp 資訊，請參閱[Tlbimp.exe （類型程式庫匯入工具）](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)和[Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 Interop 組件是[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件的橋接器之間 managed 和 unmanaged 程式碼，對應的對等項目至 COM 物件成員[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]管理成員。 Visual Basic.NET 所建立的 interop 組件可處理許多使用 COM 物件，例如封送處理的互通性的詳細資料。  
  
## <a name="interoperability-marshaling"></a>封送處理的互通性  
 所有[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式共用常見的類型，可讓互通性的物件，不論語言所使用的一組。 參數和傳回的 COM 物件的值有時候會使用與 managed 程式碼中使用的不同的資料類型。 *封送處理的互通性*是封裝參數和傳回值為對等資料類型的程序與 COM 物件中移動。 如需詳細資訊，請參閱[Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
## <a name="see-also"></a>另請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [與 Unmanaged 程式碼互通](../../../../docs/framework/interop/index.md)  
 [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (類型程式庫匯入工具)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 [Tlbexp.exe (類型程式庫匯出工具)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)  
 [免註冊的 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
