# hiddencli
process command line for administrator or root user

1. file description
    hidden.ini
        The program find this file from:
        1)current program directory or
        2)~/
        3)/etc/hidden/
        4)/etc/
        5)/etc/sysconfig/
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
        replace used in <ACTION>,
                (1)if replace="True", input cmd line not as arguments of <ACTION> node.text.
                (2)if not set replace, or set  replace="False", input cmd line not as arguments of node.text.
                (3)if node.text empty, exec the input cmd line directly.
    3)text
        text used for <ACTION>, it is callback program name, for example: <ACTION>/bin/exec_cmd</ACTION>

3. other Warning
    command line support incomplete match, for example: 'show key' can input 's k' if uniqueness.
    but some command can not differentiate them,
    for example: input 'show key' can match 'show key' and 'show keyboard', 
    in this case, can not know you want run 'show key' or 'show keyboard' command.
    therefore, if want not keep "support incomplete match", you can modify code of _hidden.

