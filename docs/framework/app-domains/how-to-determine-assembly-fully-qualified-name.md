---
title: 如何：決定組件的完整名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb5978859ba25e1595ac3da7a2d7dad8cc2cad85
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50041098"
---
# <a name="how-to-determine-an-assembly39s-fully-qualified-name"></a>如何：決定組件的完整名稱
若要在全域組件快取中找到組件的完整名稱，請使用全域組件快取工具 ([Gacutil.exe](../../../docs/framework/tools/gacutil-exe-gac-tool.md))。 請參閱[如何：檢視全域組件快取的內容](../../../docs/framework/app-domains/how-to-view-the-contents-of-the-gac.md)。  
  
 對於不在全域組件快取的組件，您可以使用數種方式取得完整組件名稱：可以使用程式碼輸出資訊至主控台或至變數，或者您可使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 以檢查組件中繼資料，其中包含完整名稱。  
  
-   如果應用程式已經載入組件時，您可以擷取 <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> 屬性的值來取得完整名稱。 您可以使用此方法，不論組件是否在 GAC 中。 這個範例將提供說明。  
  
-   如果您知道組件的檔案系統路徑，您可以呼叫靜態 (`Shared` 在 Visual Basic 中) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> 方法來取得完整組件名稱。 以下是一個簡單的範例。  
  
     [!code-csharp[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/cs/getassemblyname1.cs#1)]
     [!code-vb[System.Reflection.AssemblyName.GetAssemblyName#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflection.assemblyname.getassemblyname/vb/getassemblyname1.vb#1)]  
  
-   您可以使用 [Ildasm.exe (IL 反組譯工具)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 來檢查組件的中繼資料，其中包含完整名稱。  
  
 如需有關設定組件屬性的詳細資訊，如版本、文化特性及組件名稱，請參閱[設定組件屬性](../../../docs/framework/app-domains/set-assembly-attributes.md)。 如需有關給予組件強式名稱的詳細資訊，請參閱[建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何顯示含有指定類別組件的完整名稱至主控台。 因為它會擷取應用程式已載入組件的名稱，所以組件是否在 GAC 中並不重要。  
  
 [!code-cpp[Assembly.Fullname#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.FullName/CPP/example2.cpp#2)]
 [!code-csharp[Assembly.Fullname#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.FullName/CS/example2.cs#2)]
 [!code-vb[Assembly.Fullname#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.FullName/VB/example2.vb#2)]  
  
## <a name="see-also"></a>請參閱  
- [組件名稱](../../../docs/framework/app-domains/assembly-names.md)  
- [建立組件](../../../docs/framework/app-domains/create-assemblies.md)  
- [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
- [全域組件快取](../../../docs/framework/app-domains/gac.md)  
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [使用組件設計程式](../../../docs/framework/app-domains/programming-with-assemblies.md)
