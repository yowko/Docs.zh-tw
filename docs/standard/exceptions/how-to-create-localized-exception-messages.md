---
title: 如何：使用當地語系化例外狀況訊息來建立使用者定義的例外狀況
description: 瞭解如何使用當地語系化的例外狀況訊息來建立使用者定義的例外狀況
author: Youssef1313
ms.author: ronpet
ms.date: 09/13/2019
ms.openlocfilehash: b4aa567fccda9354bc5959d6b9838d678d53abef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696708"
---
# <a name="how-to-create-user-defined-exceptions-with-localized-exception-messages"></a>如何：使用當地語系化例外狀況訊息來建立使用者定義的例外狀況

在本文中，您將瞭解如何使用附屬元件，建立繼承自基底 @no__t 0 類別的使用者自訂例外狀況和當地語系化的例外狀況訊息。

## <a name="create-custom-exceptions"></a>建立自訂例外狀況

.NET 包含許多您可以使用的不同例外狀況。 不過，在某些情況下，如果它們都不符合您的需求，您可以建立自己的自訂例外狀況。

假設您想要建立包含 `StudentName` 屬性的 @no__t 0。
若要建立自訂例外狀況，請遵循下列步驟：

1. 建立繼承自 <xref:System.Exception> 的可序列化類別。 類別名稱的結尾應該是 "Exception"：

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception { }
    ```

1. 新增預設的構造函式：

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }
    }
    ```

1. 定義任何其他屬性和構造函式：

    ```csharp
    [Serializable]
    public class StudentNotFoundException : Exception
    {
        public string StudentName { get; }

        public StudentNotFoundException() { }

        public StudentNotFoundException(string message)
            : base(message) { }

        public StudentNotFoundException(string message, Exception inner)
            : base(message, inner) { }

        public StudentNotFoundException(string message, string studentName)
            : this(message)
        {
            StudentName = studentName;
        }
    }
    ```

## <a name="create-localized-exception-messages"></a>建立當地語系化的例外狀況訊息

您已建立自訂例外狀況，您可以使用類似下列的程式碼在任何地方擲回它：

```csharp
throw new StudentNotFoundException("The student cannot be found.", "John");
```

前一行的問題在於，`"The student cannot be found."` 只是一個常數位串。 在當地語系化的應用程式中，您想要根據使用者文化特性來擁有不同的訊息。
[附屬元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)是執行這項操作的好方法。 附屬元件是包含特定語言之資源的 .dll。 當您在執行時間要求特定資源時，CLR 會根據使用者文化特性來尋找該資源。 如果找不到該文化特性的附屬元件，則會使用預設文化特性的資源。

若要建立當地語系化的例外狀況訊息：

1. 建立名為*Resources*的新資料夾來存放資源檔。
1. 在其中加入新的資源檔。 若要在 Visual Studio 中這樣做，請在**方案總管**的資料夾上按一下滑鼠右鍵，**然後選取 [新增 @no__t**-2**新專案**]  >  個 [**資源檔**]。 將檔案命名為*ExceptionMessages .resx*。 這是預設的資源檔。
1. 新增例外狀況訊息的名稱/值組，如下圖所示：

   ![將資源新增至預設文化特性](media/add-resources-to-default-culture.jpg)

1. 新增法文的新資源檔。 將它命名*為 ExceptionMessages.fr-fr .resx*。
1. 再次新增例外狀況訊息的名稱/值組，但使用法文值：

   ![將資源新增至 fr-fr 文化特性](media/add-resources-to-fr-culture.jpg)

1. 在您建立專案之後，組建輸出檔案夾應該包含*fr-fr*資料夾，其為 *.dll*檔案，也就是附屬元件。
1. 您會擲回例外狀況，其程式碼如下所示：

    ```csharp
    var resourceManager = new ResourceManager("FULLY_QIALIFIED_NAME_OF_RESOURCE_FILE", Assembly.GetExecutingAssembly());
    throw new StudentNotFoundException(resourceManager.GetString("StudentNotFound"), "John");
    ```

  > [!NOTE]
  > 如果專案名稱為 `TestProject`，而資源檔*ExceptionMessages*位於專案的*Resources*資料夾中，則資源檔的完整名稱會是 `TestProject.Resources.ExceptionMessages`。

## <a name="see-also"></a>另請參閱

- [如何建立使用者定義的例外狀況](how-to-create-user-defined-exceptions.md)
- [建立桌面應用程式的附屬元件](../../framework/resources/creating-satellite-assemblies-for-desktop-apps.md)
- [基底C# （參考）](../../csharp/language-reference/keywords/base.md)
- [this （C#參考）](../../csharp/language-reference/keywords/this.md)
