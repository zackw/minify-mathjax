# Minify a MathJax installation

The official MathJax distribution is huge and contains a great deal of
junk you may not need.  If you want to host it yourself, as you should,
you may want to strip out all that junk.  This program does that.  The
example configuration produces a 14MB output directory from a 176MB
upstream checkout (not counting `.git`).

`minify` expects to be run, with no arguments, in a directory
containing a configuration file `minify.cfg`---such as a clean
checkout of this very repository.  Follow the instructions in
`minify.cfg` to customize its behavior to your needs.

When invoked, it will first create or update a local clone of the
MathJax Git repository, as specified in the configuration file, in a
subdirectory named `MathJax`.  It will then selectively copy files out
of that directory into a subdirectory named `MathJax.<hash>` where
<hash> is a truncated commit hash of the HEAD of the MathJax
repository (currently eight hex digits).  If a directory named
`MathJax.<hash>` already existed, it is renamed to match the updated
clone, and only the files that actually changed will be modified.
Either way, it will print out the name of the output directory upon
completion.  If `verbose` is disabled in `minify.cfg`, that is the only
output.

`minify` considers itself to own all files and directories named
`MathJax` and `MathJax.<something>` in the directory where it is
invoked.  It *will* erase and replace them as it sees fit.  You have
been warned.

Because this program includes code taken from
https://github.com/metagriffin/globre
it is distributed under the GNU General Public License,
version 3, or (at your option) any later version.
See COPYING and/or http://www.gnu.org/licenses/ for details.
The authors of this program make no copyright claim upon MathJax itself.
