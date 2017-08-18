---
title: "如何：從組件中取得類型和成員資訊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 702567b7b05f8469f796b03a59f2ead71c0a9c22
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>如何：從組件中取得類型和成員資訊
<xref:System.Reflection> 命名空間包含許多方法可以從組件中取得資訊。 本節示範其中一種方法。 如需詳細資訊，請參閱[反映概觀](../../../docs/framework/reflection-and-codedom/reflection.md)。  
  
 下列範例會從組件中取得類型和成員資訊。  
  
## <a name="example"></a>範例  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)] [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)] [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式定義域設計程式](http://msdn.microsoft.com/en-us/bd36055b-56bd-43eb-b4d8-820c37172131)   
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)   
 [使用應用程式定義域](../../../docs/framework/app-domains/use.md)

