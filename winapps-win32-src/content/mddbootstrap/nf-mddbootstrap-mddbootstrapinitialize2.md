---
UID: NF:mddbootstrap.MddBootstrapInitialize2
tech.root: bootstrap
title: MddBootstrapInitialize2
description: Initializes the calling process to use the version of the Windows App SDK framework package that best matches the specified criteria, with options. This function is intended to be used by desktop apps that are not MSIX-packaged.
ms.date: 04/22/2022
targetos: Windows
prerelease: false
req.assembly: 
req.construct-type: function
req.ddi-compliance: 
req.dll: Microsoft.WindowsAppRuntime.Bootstrap.dll
req.header: mddbootstrap.h
req.idl: 
req.include-header: 
req.irql: 
req.kmdf-ver: 
req.lib: Microsoft.WindowsAppRuntime.Bootstrap.lib
req.max-support: 
req.namespace: 
req.redist: 
req.target-min-winverclnt: Windows 10, version 1809 (with Windows App SDK 1.0 Preview 2 or later)
req.target-min-winversvr: 
req.target-type: 
req.type-library: 
req.umdf-ver: 
req.unicode-ansi: 
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - mddbootstrap.h
api_name:
 - MddBootstrapInitialize2
f1_keywords:
 - MddBootstrapInitialize2
 - mddbootstrap/MddBootstrapInitialize2
dev_langs:
 - c++
helpviewer_keywords:
 - MddBootstrapInitialize2
---

## -description

Initializes the calling process to use the version of the Windows App SDK framework package that best matches the specified criteria, with options. This function is intended to be used by desktop apps that are not MSIX-packaged.

**MddBootstrapInitialize2** offers usability and troubleshooting improvements over [**MddBootstrapInitialize**](nf-mddbootstrap-mddbootstrapinitialize.md).

Also see [Constants](/windows/windows-app-sdk/api/win32/_bootstrap/#constants).

## -parameters

### -param majorMinorVersion

Type: **UINT32**

The major and minor version of the Windows App SDK _product_ to load (e.g. 1.0).
The version is encoded as `0xMMMMNNNN`, where `M` = Major and `N` = Minor (for example, version 1.2 should be encoded as `0x00010002`).

### -param versionTag

Type: **PCWSTR**

The version tag of the Windows App SDK framework package to load (if any). For example, `"prerelease"`.

### -param minVersion

Type: **[PACKAGE_VERSION](/windows/win32/api/appmodel/ns-appmodel-package_version)**

The minimum version of the Windows App SDK _runtime_ package to use.
Note that this version (e.g. 0.319.455) is different than the Windows App SDK _release_ version (e.g. 1.0.2) and _product_ version (e.g. 1.0).

The Windows App SDK runtime version values can be obtained from the C++ header `WindowsAppSDK-VersionInfo.h`, see [Example](#example) for more details.

### -param options

Type: **[MddBootstrapInitializeOptions](ne-mddbootstrap-mddbootstrapinitializeoptions.md)**

Options for bootstrapper initialization.

## -returns

Type: **HRESULT**

If the function succeeds it returns **ERROR_SUCCESS**. Otherwise, the function returns an error code.

## -remarks

Any errors are logged to the EventLog's *Application* channel.

You can call this function multiple times provided that the parameters are compatible. The first call does the work to resolve a *Framework* package; subsequent calls are a no-op provided that the parameters are compatible with the *Framework* package resolved by the first call. If subsequent calls' parameters are not compatible, then the API fails and returns an error.

This function finds a Windows App SDK framework package that meets the specified criteria and makes the package available for use by the current process. If multiple packages meet the criteria, this function selects the best candidate.

This function must be called at startup before calling any other Windows App SDK APIs to ensure the bootstrapper component can properly initialize the Windows App SDK and add the runtime reference to the framework package.

This function also initializes the [Dynamic Dependency Lifetime Manager (DDLM)](/windows/apps/windows-app-sdk/deployment-architecture#dynamic-dependency-lifetime-manager-ddlm). The DDLM provides infrastructure to prevent the operating system (OS) from servicing the Windows App SDK framework package while it's being used by an unpackaged app.

Also see [Use the Windows App SDK runtime for non-MSIX-packaged apps](/windows/apps/windows-app-sdk/use-windows-app-sdk-run-time).

> [!NOTE]
> COM must be initialized for the current thread before you call this function.

> [!NOTE]
> If in *options* you don't specify **MddBootstrapInitializeOptions::MddBootstrapInitializeOptions_OnPackageIdentity_NOOP**, then for this API to succeed in an app that's not MSIX-packaged, it's necessary for the Windows App SDK packages to be installed on the device (see [Build and deploy a non-MSIX-packaged app that uses the Windows App SDK](/windows/apps/windows-app-sdk/tutorial-unpackaged-deployment)).

## Example

See the example in [MddBootstrapInitialize](nf-mddbootstrap-mddbootstrapinitialize.md#example).

## -see-also

* [MddBootstrap.h header](/windows/windows-app-sdk/api/win32/mddbootstrap/)
* [Constants](/windows/windows-app-sdk/api/win32/_bootstrap/#constants)
* [Use the Windows App SDK runtime for non-MSIX-packaged apps](/windows/apps/windows-app-sdk/use-windows-app-sdk-run-time)
* [Build and deploy a non-MSIX-packaged app that uses the Windows App SDK](/windows/apps/windows-app-sdk/tutorial-unpackaged-deployment)
