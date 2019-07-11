---
layout: section-page
title:  Impacts Magic
section: 03-01-02
tags: Magic
---

# MEDITECH Magic Impacts on Check-In Scripts

Version 1.0 - June 27, 2015

## Technical Overview

This documents the major items that will impact a PatientWay MEDITECH Magic integration script.

## Menu Navigation

At installation (and later upon request) PatientWay's integration software scans the menu system. We scan the main menu for the ADM and SCH modules. Then we scan all submenus of the main menu. (The example below is for the main ADM menu). When scanning certain submenus (i.e. 20 Clinical, 23 Recurring) we will do another level of scanning.

While scanning the menus templates that tell the PatientWay integration exactly what menu/screen the virtual terminal is on. We automatically ignore all text after the right-most character. This reduces the impact of menu changes when items are added.

Failure Change

If any menu text is [removed]{.underline} then the menu will not match the template and this will cause a failure in the system. For example if the menu "39. Reprint Armbands & Labels" is removed from the kiosk software's MEDITECH Menu then the system will fail.

Safe Change

If any menu text is added in the green/bold boxed areas the kiosk software will ignore this change and the menu match will succeed. For example if the menu item "150. Fubar Report" is added below "140. Fertility Services Label" the system will overlook this change.

Failure Change

If any menu text is added in the red/thin boxed areas then this will cause a failure in the kiosk system. For example if the menu "12. Fubar-Patients" is added then the menu template will not match and this will cause a failure.

**![img](assets/OzY-pFSTS1AOjvXeIilSNEXih8lOlDRx_MTqiea4yt27pbRzEe4vZydbZat6rkq5Pbfu0HL_4FnNtL-V6ZLTBwR3h3JC3g0V7OAPxa3GJ--yYBfSFOf7TX2gNTjYlRSSUQE7TeyNe-b7eEXGZg.jpeg)**



## Adding Custom Pages in CLI, RCR, SDC, etc in ADM

See the CLI screen below. The system administrator released a new page and affected some of the page numbers. The PatientWay integration uses page numbers and then expects a certain screen pattern to confirm that it is in the right place.

Before the change the script expected "Doctor & Location Information" when the page number 6 is entered. Instead it accessed the custom page for "INFECTION CONTROL CLINIC 15"

**![img](assets/alW6PqN7KeMF6Ev-pBuU-RI1-hs0KV1gp14aeujndWT7P89XvMTpiGYdcb22S_k6Tp6DPuagWbXP5Z2M8OQW7wXaitqIj8w_sf07_6n0yMTKdzVUshG0q0o4VcWXUX0XPznyuOq-L_S_VIKgUA.jpeg)**

This change requires one, optionally two, modifications. The most important modification is that page numbers for "Doctor & Location Information" and possibly "Allergies" are increased by one.

The second, optional modification, is incorporating the new page into the account extraction and account registration scripts.

Failure Change

Adding a new page in the middle of the page list. The script that fetches patient account information depends
 on "Doctor & Location Information" so adding a custom page before this page will impact the script.

Safe Change

Adding a new page to the end of the page list will be OK.

Failure Change

Reordering the page list will break the patient account fetch script.

## Adding or removing a "Custom"

Similar to menu changes, adding or removing a custom affects the standard screen pattern match templates. As well
 it will likely cause unexpected prompts or "pop-up" menus.

Failure Change

Adding or removing a custom in any ADM screen that the script uses

Safe Change

none

Potential Failure

Modifying the behavior of the custom

## Other Safe and Unsafe Changes

Safe Change

Adding login warnings and messages should be OK

Safe Change

Granting access to other modules (i.e. before: ADM and SCH, after: ADM, SCH, and BAR

List of menu items at risk (if the module is used)

-   Format is "menu" represents a menu item\
    > "adm" is the admissions module\
    > "20" is the main admissions menu number\
    > "clinical" is the first word of the menu item\
    > "12" is the submenu menu number\
    > "preregistration" is the first word of the submenu item

-   menu\_adm\_20\_clinical\_12\_preregistration\
    > menu\_adm\_20\_clinical\_13\_registration\
    > menu\_adm\_20\_clinical\_14\_registration\
    > menu\_adm\_20\_clinical\_30\_view\
    > menu\_adm\_21\_emergency\_12\_preregistration\
    > menu\_adm\_21\_emergency\_13\_registration\
    > menu\_adm\_21\_emergency\_14\_registration\
    > menu\_adm\_21\_emergency\_30\_view\
    > menu\_adm\_22\_referred\_12\_preregistration\
    > menu\_adm\_22\_referred\_13\_registration\
    > menu\_adm\_22\_referred\_14\_registration\
    > menu\_adm\_22\_referred\_30\_view\
    > menu\_adm\_23\_recurring\_12\_preregistration\
    > menu\_adm\_23\_recurring\_13\_registration\
    > menu\_adm\_23\_recurring\_14\_registration\
    > menu\_adm\_23\_recurring\_30\_view\
    > menu\_adm\_24\_surgical\_12\_preregistration\
    > menu\_adm\_24\_surgical\_13\_registration\
    > menu\_adm\_24\_surgical\_14\_registration\
    > menu\_adm\_24\_surgical\_30\_view\
    > menu\_adm\_25\_provider\_12\_preregistration\
    > menu\_adm\_25\_provider\_13\_registration\
    > menu\_adm\_25\_provider\_14\_registration\
    > menu\_adm\_25\_provider\_30\_view

