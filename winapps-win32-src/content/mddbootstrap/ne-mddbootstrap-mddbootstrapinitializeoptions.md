---
UID: NE:mddbootstrap.MddBootstrapInitializeOptions
tech.root: bootstrap
title: MddBootstrapInitializeOptions
description: Defines constants that specify options for bootstrapper initialization.
ms.date: 04/22/2022
targetos: Windows
req.construct-type: enumeration
req.ddi-compliance: 
req.header: mddbootstrap.h
req.include-header: 
req.kmdf-ver: 
req.max-support: 
req.target-min-winverclnt: Windows 10, version 1809 (with Windows App SDK 1.0 Preview 2 or later)
req.target-min-winversvr: 
req.target-type: 
req.typenames: 
req.umdf-ver: 
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - mddbootstrap.h
api_name:
 - MddBootstrapInitializeOptions
f1_keywords:
 - MddBootstrapInitializeOptions
 - mddbootstrap/MddBootstrapInitializeOptions
dev_langs:
 - c++
helpviewer_keywords:
 - MddBootstrapInitializeOptions
---

## -description

Defines constants that specify options for bootstrapper initialization with [**MddBootstrapInitialize2**](nf-mddbootstrap-mddbootstrapinitialize2.md).

## -enum-fields

### -field MddBootstrapInitializeOptions_None

Specfies no options enabled.

### -field MddBootstrapInitializeOptions_OnError_DebugBreak

Specifies that if the call is not successful then call `DebugBreak()`.

### -field MddBootstrapInitializeOptions_OnError_DebugBreak_IfDebuggerAttached

Specifies that if the call is not successful then call `DebugBreak()` if a debugger is attached to the process.

### -field MddBootstrapInitializeOptions_OnError_FailFast

Specifies that if the call is not successful then perform a fail-fast.

### -field MddBootstrapInitializeOptions_OnNoMatch_ShowUI

Specifies that if a compatible Windows App Runtime *Framework* package isn't found then show UI.

### -field MddBootstrapInitializeOptions_OnPackageIdentity_NOOP

Specifies to do nothing (don't error) if the process has package identity (MSIX-packaged and sparse-packaged apps have package identity). The default behavior is for the call to error. This option allows you to use the same compiled binary as both an MSIX-packaged and non-MSIX packaged app. The calls to Bootstrapper APIs in the MSIX-packaged binary will simply be a no-op.

## -remarks

Also see [Use the Windows App SDK runtime for non-MSIX-packaged apps](/windows/apps/windows-app-sdk/use-windows-app-sdk-run-time).

## -see-also

* [MddBootstrap.h header](/windows/windows-app-sdk/api/win32/mddbootstrap/)
* [MddBootstrapInitialize2](nf-mddbootstrap-mddbootstrapinitialize2.md)
* [Use the Windows App SDK runtime for non-MSIX-packaged apps](/windows/apps/windows-app-sdk/use-windows-app-sdk-run-time)
* [Build and deploy a non-MSIX-packaged app that uses the Windows App SDK](/windows/apps/windows-app-sdk/tutorial-unpackaged-deployment)
