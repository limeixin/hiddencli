# hiddencli
process command line for administrator or root user

1. file description
    hidden.ini
        find this file 
        1)current program directory or
        2)~/
        3)/etc/hidden/
        4)/etc/sysconfig/
    cmd_help.xml
        in hidden.ini file must mark which dir cmd_help.xml in.
2. xml file 
    cmd_help.xml use for command line, list all keys and param value and action.
    <tag attrib1=1>text</tag>tail
      1     2        3         4
    1)tag
        tag description:
        <COMMAND>   used for command key
        <PARAM>     used for param of command line
        <ACTION>    used for callback program description.
    2)attrib
        attrib description:
        must set attrib
        ---------------
        name    used in <COMMAND> for key name, and used in <PARAM> for ? info
        help    used in <COMMAND> for key description, and used in <PARAM> for param

        not must set attrib
        -------------------
        ptype   used in <PARAM> for check param value.
        replace used in <ACTION>, if replace="True", input cmd line not as arguments of <ACTION> node.text.
#        optional    used in <COMMAND> and <PARAM>, if optional="true", the cmd key or param is optional, default is false.
#        require_arg used in <COMMAND>, if require_arg="true", this cmd key must follow param. default is false.
#        interrupt   used in <ACTION> , it can "true" or "false", for interrupt cmd callback running. default is false.
#        builtin     used in <ACTION>, if if builtin="true", <ACTION> need not callback, it run user input directly.
#                    if builtin="false", it run callback program and user input as param of callback. default is false.
#        shebang     used while builtin="true" in <ACTION>, for example: shebang="/bin/bash"
    3)text
        text used for <ACTION>, it is callback program name, for example: <ACTION>exec_cmd</ACTION>


