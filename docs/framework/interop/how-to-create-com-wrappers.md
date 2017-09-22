---
title: "如何：建立 COM 包裝函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- COM,wrappers creating
- COM,wrappers Visual Studio
ms.assetid: bdf89bea-1623-45ee-a57b-cf7c90395efa
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e99b084ddb565a8ae00ee917eaf7fca2c659ab64
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-create-com-wrappers"></a>如何：建立 COM 包裝函式
您可以使用 [!INCLUDE[vsprvsext](../../../includes/vsprvsext-md.md)] 功能或 .NET Framework 工具 Tlbimp.exe 和 Regasm.exe 來建立元件物件模型 (COM) 包裝函式。 這兩種方法會產生兩種類型的 COM 包裝函式：  
  
-   型別程式庫中的[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)，會以 Managed 程式碼執行 COM 物件。  
  
-   具有所需登錄設定的 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)，會在原生應用程式中執行 Managed 物件。  
  
 在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]，您可以將 COM 包裝函式新增成為專案的參考。  
  
## <a name="wrapping-com-objects-in-a-managed-application"></a>在 Managed 應用程式中包裝 COM 物件  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-visual-studio"></a>使用 Visual Studio 建立執行階段可呼叫包裝函式  
  
1.  開啟 Managed 應用程式的專案。  
  
2.  在 [專案] 功能表上，按一下 [顯示所有檔案]。  
  
3.  在 [專案] 功能表上，按一下 [新增參考]。  
  
4.  在 [新增參考] 對話方塊中，按一下 [COM] 索引標籤，選取您要使用的元件，然後按一下 [確定]。  
  
     在方案總管中，請注意，會將 COM 元件新增至專案中的 [參考] 資料夾。  
  
 現在，您可以撰寫程式碼以存取 COM 物件。 您可以從宣告物件開始，例如使用 [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] 的 `Imports` 陳述式或是 [!INCLUDE[csprcslong](../../../includes/csprcslong-md.md)] 的 `Using` 陳述式。  
  
> [!NOTE]
>  如果您想要開發 Microsoft Office 元件，請先安裝可從 Microsoft 下載中心取得的 [Microsoft Office 主要 Interop 組件](http://go.microsoft.com/fwlink/?LinkId=50479) (PIA)。 在步驟 4 中，選取您所需之 Office 產品的最新版可用物件程式庫，例如 **Microsoft Word 11.0 物件程式庫**。  
  
#### <a name="to-create-a-runtime-callable-wrapper-using-net-framework-tools"></a>使用 .NET Framework 工具建立執行階段可呼叫包裝函式  
  
-   執行 [Tlbimp.exe (型別程式庫匯入工具)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 工具。  
  
 這項工具所建立的組件，包含原始型別程式庫中所定義之類型的執行階段中繼資料。  
  
## <a name="wrapping-managed-objects-in-a-native-application"></a>在原生應用程式中包裝 Managed 物件  
  
#### <a name="to-create-a-com-callable-wrapper-using-visual-studio"></a>使用 Visual Studio 建立 COM 可呼叫包裝函式  
  
1.  針對您要在機器碼中執行的 Managed 類別，建立類別庫專案。 此類別必須具有預設的建構函式。  
  
     確認您在 AssemblyInfo 檔案中擁有組件的完整四部分版本號碼。 這個號碼對於在 Windows 登錄中維護版本控制是必要的。 如需版本號碼的詳細資訊，請參閱[組件版本控制](../../../docs/framework/app-domains/assembly-versioning.md)。  
  
2.  在 [專案] 功能表上，按一下 [屬性]。  
  
3.  按一下 [編譯] 索引標籤。  
  
4.  選取 [註冊 COM Interop] 核取方塊。  
  
 當您建置專案時，組件會自動註冊 COM Interop。 如果您是在 [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] 中建置原生應用程式，即可在 [專案] 功能表上按一下 [新增參考] 以使用組件。  
  
#### <a name="to-create-a-com-callable-wrapper-using-net-framework-tools"></a>使用 .NET Framework 工具建立 COM 可呼叫包裝函式  
  
-   執行 [Regasm.exe (組件註冊工具)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 工具。  
  
 這項工具會讀取組件中繼資料，並將需要的項目新增至登錄。 因此，COM 用戶端便能明確地建立 .NET Framework 類別。 您可以使用與原生 COM 類別相同的方式來使用組件。  
  
 您可以對位於任何目錄中的組件執行 Regasm.exe，然後執行 [Gacutil.exe (全域組件快取工具)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) 將它移到全域組件快取中。 移動組件並不會使位置登錄項目無效，因為只要在其他位置找不到組件，就一律會對全域組件快取進行檢查。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md)   
 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md)

