---
title: COM Interop 簡介
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 7bfbf0c6de8519e91a458ab4cbb5693024cdbeb2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090387"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM Interop 簡介 (Visual Basic)

元件物件模型 (COM) 可讓物件向其他元件公開其功能，以及裝載應用程式。 雖然 COM 物件在許多方面都是 Windows 程式設計的基礎，但是針對 common language runtime (CLR) 所設計的應用程式提供許多優點。  
  
 .NET Framework 的應用程式最終會取代以 COM 開發的應用程式。 在那之前，您可能必須使用 Visual Studio 來使用或建立 COM 物件。 與 COM 或 *com interop*的互通性，可讓您使用現有的 COM 物件，並以您自己的步調轉換至 .NET Framework。  
  
 使用 .NET Framework 來建立 COM 元件時，您可以使用無註冊的 COM interop。 這可讓您在電腦上安裝多個版本時，控制已啟用的 DLL 版本，並讓使用者使用 XCOPY 或 FTP 將應用程式複製到其電腦上可執行檔適當目錄。 如需詳細資訊，請參閱 [免註冊的 COM Interop](../../../framework/interop/registration-free-com-interop.md)。  
  
## <a name="managed-code-and-data"></a>Managed 程式碼和資料  

 針對 .NET Framework 開發的程式碼稱為 managed 程式 *代碼*，其中包含 CLR 所使用的中繼資料。 .NET Framework 的應用程式所使用的資料稱為 *managed 資料* ，因為執行時間會管理與資料相關的工作，例如配置和回收記憶體以及執行類型檢查。 根據預設，Visual Basic .NET 會使用 managed 程式碼和資料，但您可以使用 interop 元件存取非受控程式碼和 COM 物件的資料， (稍後在此頁面) 所述。  
  
## <a name="assemblies"></a>組件  

 元件是 .NET Framework 應用程式的主要組建區塊。 它是一組功能的集合，可建立、建立版本，並部署為包含一或多個檔案的單一執行單位。 每個元件都包含一個組件資訊清單。  
  
## <a name="type-libraries-and-assembly-manifests"></a>類型程式庫和組件資訊清單  

 類型程式庫描述 COM 物件的特性，例如成員名稱和資料類型。 元件資訊清單對 .NET Framework 的應用程式執行相同的功能。 其中包含下列資訊：  
  
- 元件身分識別、版本、文化特性和數位簽章。  
  
- 組成元件執行的檔案。  
  
- 組成元件的類型和資源。 這包括從它匯出的檔案。  
  
- 其他元件的編譯時間相依性。  
  
- 正確執行元件所需的許可權。  
  
 如需元件和元件資訊清單的詳細資訊，請參閱 [.net 中的元件](../../../standard/assembly/index.md)。  
  
### <a name="importing-and-exporting-type-libraries"></a>匯入和匯出類型程式庫  

 Visual Studio 包含一個公用程式 Tlbimp.exe，可讓您將型別程式庫中的資訊匯入 .NET Framework 應用程式。 您可以使用 Tlbexp.exe 公用程式從元件產生類型程式庫。  
  
 如需 Tlbimp.exe 和 Tlbexp.exe 的詳細資訊，請參閱 [Tlbimp.exe (型別程式庫匯入工具) ](../../../framework/tools/tlbimp-exe-type-library-importer.md) 和 [Tlbexp.exe (型別程式庫匯出工具) ](../../../framework/tools/tlbexp-exe-type-library-exporter.md)。  
  
## <a name="interop-assemblies"></a>Interop 元件  

 Interop 元件是在 managed 和非受控碼之間橋接的 .NET Framework 元件，將 COM 物件成員對應至相等的 .NET Framework managed 成員。 Visual Basic .NET 所建立的 Interop 元件會處理許多使用 COM 物件的詳細資料，例如互通性封送處理。  
  
## <a name="interoperability-marshaling"></a>互通性封送處理  

 所有 .NET Framework 的應用程式都共用一組通用類型，可啟用物件的互通性，不論使用的程式設計語言為何。 COM 物件的參數和傳回值有時會使用與 managed 程式碼中所使用的資料類型不同的資料類型。 *互通性封送處理* 是指將參數和傳回值，在與 COM 物件來回移動的相等資料類型中封裝的程式。 如需詳細資訊，請參閱 [Interop 封送處理](../../../framework/interop/interop-marshaling.md)。  
  
## <a name="see-also"></a>另請參閱

- [COM Interop](index.md)
- [逐步解說：實作 COM 物件的繼承](walkthrough-implementing-inheritance-with-com-objects.md)
- [與 Unmanaged 程式碼互通](../../../framework/interop/index.md)
- [疑難排解互通性的問題](troubleshooting-interoperability.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [Tlbimp.exe (類型程式庫匯入工具)](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [Tlbexp.exe (類型程式庫匯出工具)](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [Interop 封送處理](../../../framework/interop/interop-marshaling.md)
- [免註冊的 COM Interop](../../../framework/interop/registration-free-com-interop.md)
