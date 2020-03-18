---
title: 如何：載入和卸載程式集
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155772"
---
# <a name="how-to-load-and-unload-assemblies"></a>如何：載入和卸載程式集
程式引用的程式集將自動由通用語言運行時載入，但也可以動態地將特定程式集載入到當前應用程式域中。 有關詳細資訊，請參閱[如何：將程式集載入到應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)中。

在 .NET 框架中，如果不卸載包含它的所有應用程式域，就無法卸載單個程式集。 即使組件超出範圍，實際組件檔仍會保持載入狀態，直到卸載所有包含該組件的應用程式定義域為止。 在 .NET Core<xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType>中，類處理常式集的卸載。 有關詳細資訊，請參閱如何在[.NET Core 中使用和偵錯工具集卸載。](unloadability.md)

## <a name="load-and-unload-assemblies"></a>載入和卸載組件

要將程式集載入到應用程式域中，請使用 類<xref:System.AppDomain>和<xref:System.Reflection.Assembly>中包含的幾種載入方法之一。 有關詳細資訊，請參閱[如何：將程式集載入到應用程式域](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)中。 請注意，.NET Core 僅支援單個應用程式域。

要卸載 .NET 框架中的程式集，必須卸載包含它的所有應用程式域。 要卸載應用程式域，請使用 方法<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>。 有關詳細資訊，請參閱[操作：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。

如果要卸載一些程式集，而不是 .NET Framework 應用程式中的其他程式集，請考慮創建新的應用程式域，在域中執行代碼，然後卸載該應用程式域。 有關詳細資訊，請參閱[操作：卸載應用程式域](../../framework/app-domains/how-to-unload-an-application-domain.md)。  

## <a name="see-also"></a>另請參閱

- [C# 程式設計指南](../../csharp/programming-guide/index.md)
- [程式設計概念（視覺基礎）](../../visual-basic/programming-guide/concepts/index.md)
- [.NET 中的組件](index.md)
- [如何：將程式集載入到應用程式域中](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
