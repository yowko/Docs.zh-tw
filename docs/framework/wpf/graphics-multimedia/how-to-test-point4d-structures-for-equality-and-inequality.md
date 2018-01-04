---
title: "如何：測試 Point4D 結構是否相等和不相等"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac69ec232485ebd3097f2db3b31d3fd43d0ccc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>如何：測試 Point4D 結構是否相等和不相等
這個範例示範如何測試<xref:System.Windows.Media.Media3D.Point4D>結構相等和不等。  
  
 下列程式碼說明如何測試<xref:System.Windows.Media.Media3D.Point4D>結構進行相等和不等比較使用<xref:System.Windows.Media.Media3D.Point4D>等號比較方法。  <xref:System.Windows.Media.Media3D.Point4D>結構的測試方式，使用多載等號比較是否相等 (`==`) 運算子，然後使用多載不等比較的不等比較 (`!=`) 運算子，最後再<xref:System.Windows.Media.Media3D.Point3D>結構和<xref:System.Windows.Media.Media3D.Point4D>結構會檢查是否有使用靜態等號比較<xref:System.Windows.Media.Media3D.Point4D.Equals%2A>方法。  
  
## <a name="example"></a>範例  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
