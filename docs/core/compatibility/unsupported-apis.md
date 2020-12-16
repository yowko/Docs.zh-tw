---
title: .NET Core 和 .NET 5 + 上不支援的 Api
titleSuffix: ''
description: 瞭解哪些 .NET Api 一律會在 .NET Core 和 .NET 5.0 和更新版本上擲回例外狀況。
ms.date: 10/13/2020
ms.openlocfilehash: 1bd41192d0d6752d2b659da9fb6387dac321b2c3
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593262"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a>在 .NET Core 和 .NET 5 + 上一律會擲回例外狀況的 Api

下列 Api 一律會 <xref:System.PlatformNotSupportedException> 在 .net 5.0 和更新版本上擲回， (包括所有或平臺子集上的所有 .Net Core 版本) 。

本文會依命名空間來組織受影響的 Api。

> [!NOTE]
>
> - 本文是進行中的工作。 它不是在 .NET 5 + 上擲回例外狀況的完整 Api 清單。
> - 本文不包含在 .NET 5 + 上擲回之二進位序列化的明確介面執行。 如需詳細資訊，請參閱 [.Net Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)。

## <a name="system"></a>System

| member | 擲回的平臺 |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | 全部 |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | 全部 |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 全部 |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 全部 |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | 全部 |

## <a name="systemcodedomcompiler"></a>System.CodeDom.Compiler

| member | 擲回的平臺 |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | 全部 |

## <a name="systemcollectionsspecialized"></a>System.Collections.Specialized

| member | 擲回的平臺 |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | 全部 |

## <a name="systemconfiguration"></a>System.Configuration

| member | 擲回的平臺 |
| - | - |
| <xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (所有成員)  | 全部 |

## <a name="systemconsole"></a>System.Console

| member | 擲回的平臺 |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Console.BufferHeight?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.BufferWidth?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.CursorSize?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.CursorVisible?displayProperty=nameWithType> (只取得)  | Linux 與 macOS |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Console.Title?displayProperty=nameWithType> (只取得)  | Linux 與 macOS |
| <xref:System.Console.WindowHeight?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.WindowLeft?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.WindowTop?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Console.WindowWidth?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |

## <a name="systemdatacommon"></a>System.Data.Common

| member | 擲回的平臺 |
| - | - |
| <xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (擲回 <xref:System.NotSupportedException>)  | 全部 |

## <a name="systemdiagnosticsprocess"></a>System.Diagnostics.Process

| member | 擲回的平臺 |
| - | - |
| <xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> 僅 (設定)  | Linux |
| <xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> 僅 (設定)  | Linux |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | macOS |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.Process.Start(System.String,System.String,System.Security.SecureString,System.String)?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (只取得)  | macOS |
| <xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |

## <a name="systemio"></a>System.IO

| member | 擲回的平臺 |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |

## <a name="systemiopipes"></a>System.IO.Pipes

| member | 擲回的平臺 |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> 僅 (設定)  | Linux 與 macOS |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | Linux 與 macOS |

## <a name="systemmedia"></a>System. Media

| member | 擲回的平臺 |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |

## <a name="systemnet"></a>System.Net

| member | 擲回的平臺 |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |

## <a name="systemnetnetworkinformation"></a>System.Net.NetworkInformation

| member | 擲回的平臺 |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | Windows (UWP)  |

## <a name="systemnetsockets"></a>System.Net.Sockets

| member | 擲回的平臺 |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | 全部 |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | 全部 |

## <a name="systemnetwebsockets"></a>System.Net.WebSockets

| member | 擲回的平臺 |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | 全部 |

## <a name="systemreflection"></a>System.Reflection

| member | 擲回的平臺 |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | 全部 |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | 全部 |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | 全部 |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | 全部 |

## <a name="systemruntimecompilerservices"></a>System.Runtime.CompilerServices

| member | 擲回的平臺 |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | 全部 |

## <a name="systemruntimeinteropservices"></a>System.Runtime.InteropServices

| member | 擲回的平臺 |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | 全部 |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | 全部 |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | 全部 |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | 全部 |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | Linux 與 macOS |

## <a name="systemruntimeserialization"></a>System.Runtime.Serialization

| member | 擲回的平臺 |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | 全部 |

## <a name="systemsecurity"></a>System.Security

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | 全部 |

## <a name="systemsecurityclaims"></a>System.Security.Claims

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | 全部 |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |

## <a name="systemsecuritycryptography"></a>System.Security.Cryptography

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | Linux 與 macOS |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | 全部 |

## <a name="systemsecuritycryptographypkcs"></a>System.Security.Cryptography.Pkcs

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | 全部 |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | 全部 |

## <a name="systemsecuritycryptographyx509certificates"></a>System.Security.Cryptography.X509Certificates

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> 僅 (設定)  | 全部 |

## <a name="systemsecurityauthenticationextendedprotection"></a>System.Security.Authentication.ExtendedProtection

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |

## <a name="systemsecuritypolicy"></a>系統安全性原則

| member | 擲回的平臺 |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |

## <a name="systemserviceprocessservicecontroller"></a>System.ServiceProcess.ServiceController

| member | 擲回的平臺 |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | 全部 |

## <a name="systemtextregularexpressions"></a>System.Text.RegularExpressions

| member | 擲回的平臺 |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | 全部 |

## <a name="systemthreading"></a>System.Threading

| member | 擲回的平臺 |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | 全部 |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | 全部 |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | 全部 |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | 全部 |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | 全部 |

## <a name="systemxml"></a>System.Xml

| member | 擲回的平臺 |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | 全部 |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | 全部 |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | 全部 |

## <a name="see-also"></a>另請參閱

- [從 .NET Framework 遷移至 .NET Core 的重大變更](fx-core.md)
- [.NET Core 中的二進位序列化](../../standard/serialization/binary-serialization.md#net-core)
- [.NET 可攜性分析器](../../standard/analyzers/portability-analyzer.md)
