# NAME

beacon\_yaml2md: Script to convert Beacon v2 Model schemas to Markdown

# SYNOPSIS

beacon\_yaml2md.pl

     Options:
       -schema-dir                    Directory with YAML schemas
       -markdown-dir                  Directory where to write .md
       -D|delete                      Delete schema-dir/obj/*yaml
       -h|help                        Brief help message
       -man                           Full documentation
       -debug                         Print debugging (from 1 to 5, being 5 max)
       -verbose                       Verbosity on

# CITATION

To be defined.

# SUMMARY

beacon\_yaml2md: Script to convert Beacon v2 Model schemas to Markdown

**NOTE:** This script is **UNDER CONSTRUCTION** and improvements are added often.

# MOTIVATION

Prior to the creation of this script (i.e.,June-2021), the Beacon documentation for the schemas was first created in a text-type document (e.g., Word) and then MANUALLY transformed into
YAMLs schemas. Each time the original MS Word document was edited, someone had to manually edit the YAML.

This script inverts the process, i.e., **it enforces modifying the schema specification directly at the YAML/JSON level**.

Editing the schemas directly at the YAML/JSON leven has two advantages, the first is that (because we follow [OpenAPI](https://swagger.io/specification/) specifications) the endpoints documentation can be directly displayed with [SWAGGER UI](https://ga4gh-approval-service-registry.ega-archive.org). The second is that the YAML/JSON files can be converted to Markdown tables in order to create [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest/) documentation. This script **transforms YAML/JSON to Markdown tables**, including their nested objects up to a third degree of hierarchy.

The **Markdown** format can be directly rendered as tables at the [GitHub repository](https://github.com/mrueda/beacon-schema-2/tree/main/docs/schemas-md), and it can be used  with [MkDocs](https://www.mkdocs.org/) to create  [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest/) documentation. 

Everytime a `git push` is performed to the [repo](https://github.com/mrueda/beacon-schema-2) the documentation at [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest/) gets updated. Note that only content under directory `docs/` will make it to [Read The Docs](https://beacon-schema-2.readthedocs.io/en/latest/).

Before creating this tool, the author made an exhaustive search on what had been dveloped by the _community_ to automatically convert YAML/JSON to Markdown tables and found that there were many ways to go from YAML/JSON to HTML (e.g., CPAN, Python, Node.js), but not much from YAML/JSON to Markdown. Obviously, even in the case we had found something, some major tweaking will be needed in order to display things the way we want.

In the Beacon context, _mbaudis_ has developed a nice framework for [schemablocks](https://github.com/ga4gh-schemablocks/schemablocks-tools) which creates HTML from YAML schemas to be used with [Yekyll](https://jekyllrb.com/). However, personalizing his tools to work in our scenario will still not solve the initial objective of creating Markdown tables from the YAML/JSON.

All of the above lead to the creation of this tool, which was written in [Perl](https://www.perl.org) language.

# HOW TO RUN BEACON\_YAML2MD

The script is written in Perl and runs on Linux (tested on Debian-based distribution). Perl 5 is installed by default on Linux, 
but you might need to manually install the below CPAN module(s).

    * YAML::XS
    * JSON::XS
    * Path::Tiny

First we install cpanminus (with sudo privileges):

    $ sudo apt-get install cpanminus

Then the module(s):

    $ cpanm --sudo YAML::XS JSON::XS Path::Tiny

The script takes YAMLs as input file and when no arguments is used it will read them from `../schemas/` directory.

**NB:** We recommend running the script with the provided bash file `transform_yaml2md.sh` (**see ADDENDUM: How to update Read The Docs documentation**).

**Example 1:**

    $ ./beacon_yaml2md.pl 

If the script is run directly at `bin/` directory (default) and with no arguments, then it will create contents in:

    * YAMLs at ../schemas/
    * Markdowns at ../docs/schemas-md/

**Example 2:**

Here we are providind arguments for --schema-dir and for markdown-dir.

    $ $path/beacon_yaml2md.pl --schema-dir ../schemas --markdown-dir ../docs/schemas-md --D

_NB:_ if the YAML is not well defined (e.g., wrong indentation, etc.) the script will complain about it. Thus, it indirectly serves as a YAML validator.

**Notes:**

The argument `-D|delete` deletes all `../schemas/obj/*yaml` files prior to doing anything else. It's harmless so you may want to use it you're unsure of who created those files.

See the directory tree below:

```` 
```
 beacon-schema-2/
 |-- bin
 |-- docs
 |   |-- img
 |   `-- schemas-md
 |       `-- obj
 `-- schemas
     `-- obj
```
 ````

_NB:_ The script was built to work with the Beacon v2 Model schemas and the author deliberately chose to hard-code some variables (e.g., the _schemas_) to avoid extra arguments or a config.file. However, this may change in future versions depending on user's adoption/feedback.

_NB:_ The decission to take YAMLs (and not JSON) as an input is deliberate and made by the author.

## ADDENDUM: How to update Read The Docs documentation

There are several steps that need to be peformed to update readthedocs:

    1 - Clone or download:

      a ) Beacon v2 Models from L<Github|https://github.com/ga4gh-beacon/beacon-v2-Models>.

      b ) Beacon framework v2 from L<Github|https://github.com/ga4gh-beacon/beacon-framework-v2>.

    2 - Install C<jsonref> and C<jq>.

       $ sudo pip3 install jsonref #  Python 2 => sudo pip install jsonref

       The reason for installing this tool is that we need it to convert JSON files with JSON references ($ref) to JSON files with no references (i.e., all references will be embeded in the file).

       $ sudo apt-get install jq

       Tool needed to parse JSON files.

    3 - Modify the two variables 'mod_dir' and 'fw_dir' inside transform_json2md.sh according to the paths from Step 1:
        
    4 - Inside 'bin' directory run:

      $ ./transform_json2md.sh

      $ cd ..
      
      $ git add schemas docs 

    5 - Finally you need to push beacon-schema-2 repo to GitHub.

    6 - Readthedocs should be updated.

# AUTHOR 

Written by Manuel Rueda, PhD. Info about EGA can be found at [https://ega-archive.org/](https://ega-archive.org/).

# REPORTING BUGS

Report bugs or comments to <manuel.rueda@crg.eu>.

# COPYRIGHT

This PERL file is copyrighted. See the LICENSE file included in this distribution.
