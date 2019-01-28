---
title: 組件和並存執行
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b635dcbbb3a78948a2d1d1e9d4feca6f4d2ee76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657996"
---
# <a name="assemblies-and-side-by-side-execution"></a>組件和並存執行
並存執行是可以在同一台電腦上儲存和執行多版應用程式或元件的能力。 這表示您可以同時在同一台電腦上擁有多版執行階段、多版應用程式和多個使用一個執行階段版本的元件。 並存執行讓您可以進一步控制應用程式繫結到的元件版本，也能進一步控制應用程式所使用的執行階段版本。  
  
 支援並存儲存和執行同一組件的不同版本，是強式命名所不可或缺的部分，而且已內建至執行階段的基礎結構中。 由於強式名稱組件的版本號碼是其識別的一部分，所以執行階段可以在全域組件快取中存放相同組件的多個版本，並且在 Run Time 載入這些組件。  
  
 雖然執行階段為您提供建立並存應用程式的能力，但是並存執行並非自動的。 如需建立並存執行應用程式的詳細資訊，請參閱[建立並存執行元件的方針](../../../docs/framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。  
  
## <a name="see-also"></a>另請參閱
- [執行階段如何找出組件](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
