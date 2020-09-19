# SPDX Python Library for LicenseMatching
A Python Library to implement SPDX License Matching. This Project is a result of CommunityBridge Linux Foundation 2020 contribution by [@anshuldutt21](https://github.com/anshuldutt21/).

Home: https://github.com/anshuldutt21/spdx_python_licensematching/

Issues: https://github.com/anshuldutt21/spdx_python_licensematching/issues

# License
[Apache-2.0](https://github.com/spdx/tools-python/blob/master/LICENSE)

# Features

*    An Interface which will check text against a license template using the license matching guidelines.
*    An Interface which will check text and return all matching SPDX listed license ID's.
*    An interface which takes 2 license texts as input and returns a boolean indicating if the 2 licenses match per the license matching guidelines.
*    When there is not a match, a return value provided making it possible to describe where and why the license does not match.

# Installation

As always you should work in a virtualenv or venv. Do the following steps to setup the Python Package in your system.

```bash
git clone https://github.com/anshuldutt21/spdx_python_licensematching.git
cd spdx_python_licensematching
pip install -e .
```

# How To Use

## Match 2 License Texts
License Texts are matched based on the [SPDX License Matching Guidelines](https://spdx.dev/license-list/matching-guidelines/). In order to implement License Matching between 2 License Texts, do the following steps.

Input all the Text Files you want to match at the `input_text_files` directory inside `normalize_license_text`. This can be done by the following steps.

```bash
mv <TextFile_A> normalize_license_text/input_text_files 
mv <TextFile_B> normalize_license_text/input_text_files 
```

To match  TextFile_A and TextFile_B execute the file normalize.py in the following way.

```python
python normalize_license_text/normalize.py <TextFile_A> <TextFile_B>
```
After this step you would get an output depicting whether the license Textfiles match or not along with the text describing the mismatch possibilities.

## Match a License Text with a License Template
License templates are implemented on the basis of the [SPDX License Matching Guidelines](https://spdx.dev/license-list/matching-guidelines/). In order to use the feature  of comparing a license text and a template, do the following steps.

Input all the Text Files and the Template files at the `input_text_files` and the `input_template_files` directory respectively inside `compare_license_template`.  This can be done by the below steps.

```bash
mv <TextFile_A> compare_template_text/input_text_files
mv <TemplateFile_A> compare_template_text/input_template_files
```

To match TextFile_A and TemplateFile_A execute the file compare_normalized_files.py in the following way.

```python
python compare_template_text.py/compare_template_text.py <TextFile_A> <TemplateFile_A>
```

After this step you would get an output depicting whether the license Textfiles match with the License Template or not along with the text describing the mismatch possibilities.

## Match a license Text against all License templates.

The match_against_all_templates folder implements matching of the input license text against all the data templates in the SPDX license data. To match a License Text against all the License Templates, do the following steps:

Input all the Text Files you want to match at the ` input_text_files` directory inside `match_against_all_templates`. This can be done by the following steps.

```bash
mv <TextFile_A> match_against_all_templates/input_text_files
```

To match TextFile_A against all templates execute the file match_all_ids.py.py in the following way.

```python
python match_all_ids.py <TextFile_A>
```

# Tests

In order to run tests run 

```python
python setup.py test
```

# Development process

We use the GitHub flow that is described here: https://guides.github.com/introduction/flow/

So, whenever we have to make some changes to the code, we should follow these steps:
1. Create a new branch:
    `git checkout -b fix-or-improve-something`
2. Make some changes and the first commit(s) to the branch: 
    `git commit --signoff -m 'What changes we did'`
3. Push the branch to GitHub:
    `git push origin fix-or-improve-something`
4. Make a pull request on GitHub.
5. Continue making more changes and commits on the branch, with `git commit --signoff` and `git push`.
6. When done, write a comment on the PR asking for a code review.
7. Some other developer will review your changes and accept your PR. The merge should be done with `rebase`, if possible, or with `squash`.
8. The temporary branch on GitHub should be deleted (there is a button for deleting it).
9. Delete the local branch as well:
    ```
    git checkout master
    git pull -p
    git branch -a
    git branch -d fix-or-improve-something
    ```

Besides this, another requirement is that every change should be made to fix or close an issue: https://guides.github.com/features/issues/
If there is no issue for the changes that you want to make, create first an issue about it that describes what needs to be done, assign it to yourself, and then start working for closing it.

# Dependencies

* Difflib : https://docs.python.org/3/library/difflib.html used for generating differences.
* Re : https://docs.python.org/3/library/re.html for handling regexes.
