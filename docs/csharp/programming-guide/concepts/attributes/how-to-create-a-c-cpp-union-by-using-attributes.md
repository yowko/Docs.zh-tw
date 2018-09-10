---
title: 如何：使用屬性建立 C-C++ 等位 (C#)
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 8b5a88656b1172407c3e5b9f5198d5acae7bf9e0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43798505"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a>如何：使用屬性建立 C/C++ 等位 (C#)
您可以使用屬性，自訂如何在記憶體中配置結構。 例如，您可以使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 屬性，以 C/C++ 建立所謂的等位。  
  
## <a name="example"></a>範例  
 在此程式碼片段中，`TestUnion` 的所有欄位都在記憶體的同一位置開始。  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestUnion  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public byte b;  
       }  
```  
  
## <a name="example"></a>範例  
 以下是另一個範例，欄位從明確設定的不同位置開始。  
  
```csharp  
// Add a using directive for System.Runtime.InteropServices.  
  
       [System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]  
       struct TestExplicit  
       {  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public long lg;  
  
           [System.Runtime.InteropServices.FieldOffset(0)]  
           public int i1;  
  
           [System.Runtime.InteropServices.FieldOffset(4)]  
           public int i2;  
  
           [System.Runtime.InteropServices.FieldOffset(8)]  
           public double d;  
  
           [System.Runtime.InteropServices.FieldOffset(12)]  
           public char c;  
  
           [System.Runtime.InteropServices.FieldOffset(14)]  
           public byte b;  
       }  
```  
  
 `i1` 和 `i2` 這兩個整數欄位和 `lg` 共用相同的記憶體位置。 使用平台叫用時，這種結構配置控制項很有用。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Reflection>  
- <xref:System.Attribute>  
- [C# 程式設計指南](../../../../csharp/programming-guide/index.md)  
- [屬性](../../../../../docs/standard/attributes/index.md)  
- [反映 (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [建立自訂屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
- [使用反射存取屬性 (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
