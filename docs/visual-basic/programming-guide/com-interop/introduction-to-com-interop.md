---
title: COM Interop 簡介 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 639b621215f25bc1042274a92a21fca2985e5918
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244110"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Interop 簡介 (Visual Basic)
元件物件模型 (COM) 可讓您公開其功能給其他元件和主控件應用程式的物件。 雖然 COM 物件已被 Windows 程式設計許多年的基礎，專為 common language runtime (CLR) 所設計的應用程式會提供許多優點。  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 應用程式最終會取代這些開發 com。 在那之前，您可能要使用，或使用 Visual Studio 建立 COM 物件。 與 COM 互通性或*COM interop*，可讓您使用現有的 COM 物件轉換成[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]您自己的步調。  
  
 使用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]若要建立 COM 元件，您可以使用免註冊 COM interop。 這可讓您控制哪些 DLL 版本已啟用時的電腦上，安裝一個以上的版本，而且可讓使用者可以使用 XCOPY 或 FTP 複製到他們的電腦上的適當目錄的應用程式可以執行它。 如需詳細資訊，請參閱 <<c0> [ 免註冊 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)。  
  
## <a name="managed-code-and-data"></a>Managed 程式碼和資料  
 針對開發的程式碼[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]指*managed 程式碼*，且包含 CLR 所使用的中繼資料。 所使用的資料[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式會呼叫*受管理的資料*因為執行階段會管理資料相關工作，例如配置和回收記憶體，以及執行類型檢查。 根據預設，Visual Basic.NET 使用 managed 程式碼和資料，但您可以存取 unmanaged 程式碼和資料的 COM 物件使用 interop 組件 （在此頁面稍後說明）。  
  
## <a name="assemblies"></a>組件  
 組件為主要建置組塊的[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 它是功能，可建置、 版本設定，以及部署為包含一或多個檔案的單一實作單元的集合。 每個組件包含組件資訊清單。  
  
## <a name="type-libraries-and-assembly-manifests"></a>型別程式庫和組件資訊清單  
 型別程式庫描述 COM 物件，例如成員名稱和資料類型的特性。 組件資訊清單執行的相同函式[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 其中包括下列資訊：  
  
-   組件身分識別、 版本、 文化特性和數位簽章。  
  
-   構成組件實作的檔案。  
  
-   型別和構成組件的資源。 這包括從其匯出。  
  
-   對其他組件的編譯時間相依性。  
  
-   若要正確執行的組件所需的權限。  
  
 如需有關組件和組件資訊清單的詳細資訊，請參閱 <<c0> [ 組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)。  
  
### <a name="importing-and-exporting-type-libraries"></a>匯入和匯出類型程式庫  
 Visual Studio 包含的公用程式，可讓您從類型程式庫匯入資訊的 Tlbimp[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式。 您可以使用 Tlbexp 公用程式，從組件產生類型程式庫。  
  
 如需 Tlbimp 和 Tlbexp 資訊，請參閱[Tlbimp.exe （型別程式庫匯入工具）](../../../framework/tools/tlbimp-exe-type-library-importer.md)並[Tlbexp.exe （類型程式庫匯出工具）](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)。  
  
## <a name="interop-assemblies"></a>Interop 組件  
 Interop 組件都會[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]的橋接器之間受控和非受控組件程式碼的對等項目對應 COM 物件成員[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]管理成員。 Visual Basic.NET 所建立的 interop 組件可處理許多使用 COM 物件，例如交互操作性封送處理的詳細資料。  
  
## <a name="interoperability-marshaling"></a>互通性封送處理  
 所有[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]應用程式共用一組常見的類型，可讓物件，不論使用的程式設計語言的互通性。 參數和傳回值的 COM 物件有時會使用不同的 managed 程式碼中所使用的資料類型。 *互通性封送處理*移動的 COM 物件會封裝參數和傳回的值為對等的資料類型的程序。 如需詳細資訊，請參閱 < [Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
## <a name="see-also"></a>另請參閱  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)  
 [逐步解說：實作 COM 物件的繼承](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)  
 [互通性的疑難排解](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (類型程式庫匯出工具)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)  
 [免註冊的 COM Interop](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
