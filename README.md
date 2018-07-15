# Tampermonkey_textage
譜面をひとつなぎにします。

    // ==UserScript==
    // @name         Textage
    // @namespace    http://tampermonkey.net/
    // @version      0.1
    // @description  Tampermonkey scripts jumps over the crap codes.
    // @author       sequre
    // @match        http://textage.cc/score/*
    // @grant        none
    // ==/UserScript==
    "use strict";

    (() =>
    {
        const parentTr = document.querySelectorAll("body > table > tbody > tr")[0];
        const childTd = document.querySelectorAll("body > table > tbody > tr > td");
        const replaceTd = document.createElement("td");
        let childTable;
        let i, j;

        for(i = 0; i < childTd.length; i++)
        {
            childTable = childTd[i].getElementsByTagName("table");
            if(childTable.length < 1)continue;
            for(j = childTable.length - 1; j >= 0 ; j--)
            {
                parentTr.parentNode.insertBefore(childTable[j], parentTr.parentNode.firstElementChild);
            }
        }
    })();
