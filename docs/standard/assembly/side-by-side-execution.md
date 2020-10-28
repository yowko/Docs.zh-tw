---
title: 組件和並存執行
description: 深入瞭解並存執行，這是在同一部電腦上儲存和執行多個版本之應用程式或元件的能力。
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET]
- assemblies [.NET], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 7bedd5a384ceace014412eb894adad5c92c00b05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687980"
---
# <a name="assemblies-and-side-by-side-execution"></a>組件和並存執行

並存執行是可以在同一台電腦上儲存和執行多版應用程式或元件的能力。 這表示您可以同時在同一台電腦上擁有多版執行階段、多版應用程式和多個使用一個執行階段版本的元件。 並存執行讓您可以進一步控制應用程式繫結到的元件版本，也能進一步控制應用程式所使用的執行階段版本。  
  
支援並存儲存和執行同一組件的不同版本，是強式命名所不可或缺的部分，而且已內建至執行階段的基礎結構中。 由於強式名稱組件的版本號碼是其識別的一部分，所以執行階段可以在全域組件快取中存放相同組件的多個版本，並且在 Run Time 載入這些組件。  
  
雖然執行階段為您提供建立並存應用程式的能力，但是並存執行並非自動的。 如需有關建立並存執行之應用程式的詳細資訊，請參閱 [建立並存執行元件的指導方針](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md)。  
  
## <a name="see-also"></a>請參閱

- [執行時間如何找出元件](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [.NET 中的組件](index.md)
