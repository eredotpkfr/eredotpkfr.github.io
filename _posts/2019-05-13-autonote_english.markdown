---
layout: post
title:  "What is autonote.sh?"
date:   2019-05-13 10:26:23 +0300
categories: english_topics projects
tags: ubuntu script bash bash_script
---
# autonote.sh
If you often taking note like me, you wanna backup your notes. I thought this subject and I wrote Bash Script about this subject. If you wonder script details, you can find [script's github page](https://github.com/eredotpkfr/autonote.sh){: target="_blank"}. Script's usage and configurations on [youtube!](https://www.youtube.com/watch?v=3x0NBIHnO4s){: target="_blank"}
<br/>
# Script's content

{% highlight bash linenos %}
#!/bin/bash

# AUTHOR: Eredot_PK&FR       0=={::::::::::::>

function delete_files(){
    deleted_files=`git status | grep "deleted:" | awk '{print $2}'`
    if [ ! -z "$deleted_files" ]; then
        zenity --question --width 333 --text=\
    "Are you sure ? Do you want to delete this/these files \
    ?\n $(echo -n $deleted_files | tr ' ' '\t')"
        if [ $? -eq 0 ]; then
            git rm $deleted_files
        else :
    fi
    else :
    fi }

function push_files(){
    cd /home/eredot_pkfr/n0t3s/notes/ && git add *
    if [[ "`git status`" == *"nothing to commit"* ]]; then
        if [[ "`git status`" == *"nothing to commit"* && \
    "`git status`" == *"(use \"git push\" to publish \
    your local commits)"* ]]; then
	    git push -u origin master --force
            notify-send "AUTONOTE - Your Repository Is UP-TO-DATE"
    else
	    notify-send "AUTONOTE - Nothing To Commit      /      \
        Nothing To Change"
        fi
    else
        delete_files
    git commit -m "`date`" && git push -u origin master --force
    if [ $? -eq 0 ]; then
	    notify-send "AUTONOTE - Your Repository Is UP-TO-DATE"
    else
	    notify-send "AUTONOTE - Files Are Not Pushing ..."
    fi
        #new_files=`git status | grep "new file:" | awk '{print $2}'`
        #git commit -m "`date`" && git push -u origin master
    fi }

wget -q --spider https://www.google.com/
if [ $? -eq 0 ]; then
    notify-send "AUTONOTE - ONLINE      /      Starting Script ..."
    push_files
else
        notify-send "AUTONOTE - OFFLINE      /      \
    Script Failed To Start ..."
fi
{% endhighlight %}
