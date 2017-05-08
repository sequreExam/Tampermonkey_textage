# Tampermonkey_textage
    // ==UserScript==
    // @name         Textage
    // @namespace    http://tampermonkey.net/
    // @version      0.1
    // @description Tampermonkey scripts jumps over the crap codes.
    // @author       sequre
    // @match        http://textage.cc/score/*
    // @grant         none
    // @require      https://ajax.googleapis.com/ajax/libs/jquery/3.1.0/jquery.min.js
    // ==/UserScript==

    (function()
    {
        'use strict';

        // Your code here...
        var parentTable = $("body > table > tbody > tr");
        var childTd = $("body > table > tbody > tr > td");
        var childTable = $();
        var replaceArea = $("body > table > tbody > tr > td > img");
        var DOM = $();
        var i, j;

        console.log(childTd.length); // 16
        for(i = 0; i < childTd.length; i++)
        {
            childTable = childTd.eq(i).find("table");
            console.log(childTable.length); // 3, 4, 4, ... , 5
            for(j = childTable.length - 1; j >= 0 ; j--)
            {
                replaceArea.prepend($(childTable).eq(j));
            }
        }

        DOM = replaceArea.wrapInner("<td />").wrapInner("<tr />").children();
        DOM.replaceAll(parentTable);
    })();
