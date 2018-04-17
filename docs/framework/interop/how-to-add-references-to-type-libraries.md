---
title: 如何：將參考加入至類型程式庫
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 561e05c82c1882ad5e495ddb3dc1a17356522514
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-references-to-type-libraries"></a>如何：將參考加入至類型程式庫
Visual Studio 會產生內含新增類型程式庫參考時所產生之中繼資料的 interop 組件。 如有提供主要的 Interop 組件，Visual Studio 便會先使用現有的組件，然後再產生新的 Interop 組件。  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a>新增 Visual Studio 中之類型程式庫的參考  
  
1.  若 Windows Setup.exe 未在您的電腦上安裝 COM DLL 或 EXE 檔案，請自行安裝。  
  
2.  依序選擇 [專案] 及 [新增參考]。  
  
3.  在 [參考管理員] 中，選擇 [COM]。  
  
4.  從清單中選取類型程式庫，或瀏覽至 .tlb 檔案。  
  
5.  選擇 [確定] 。  
  
6.  在方案總管中，開啟所新增之參考的捷徑功能表，然後選擇 [屬性]。  
  
7.  在 [屬性] 視窗中，確定**內嵌 Interop 類型**屬性已設為 [True]。 這可讓 Visual Studio 將 COM 類型的類型資訊嵌入您的可執行檔中，免除將主要 Interop 組件部署到應用程式的動作。  
  
> [!NOTE]
>  功能表與對話方塊可能會隨您所使用的 Visual Studio 版本而不同。  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a>新增類型程式庫參考供命令列編譯時使用  
  
1.  產生[如何：從型別程式庫產生 Interop 組件](how-to-generate-interop-assemblies-from-type-libraries.md)中所述的 Interop 組件。  
  
2.  使用 [/link (C# 編譯器選項)](../../csharp/language-reference/compiler-options/link-compiler-option.md) 或 [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) 編譯器選項加上 Interop 組件名稱，將 COM 類型的類型資訊嵌入您的可執行檔中。  
  
## <a name="see-also"></a>另請參閱  
 [匯入類型程式庫做為組件](importing-a-type-library-as-an-assembly.md)  
 [將 COM 元件公開給 .NET Framework](exposing-com-components.md)  
 [逐步解說：從 Microsoft Office 組件內嵌類型資訊](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))  
 [逐步解說：從 Managed 組件內嵌類型](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [/link (C# 編譯器選項)](../../csharp/language-reference/compiler-options/link-compiler-option.md)  
 [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md)
