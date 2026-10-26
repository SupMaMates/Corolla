# The Corolla mindset

**Keep it stupid simple. Everywhere.**

This owner direction applies to every part of Corolla: architecture, code,
dependencies, panel screens, installation, everyday use, updates, recovery,
operations, testing, documentation, releases and how contributors work together.

- **Reuse first.** Follow useful XC_VM behavior and maintained public tools before
  building a replacement. A difference needs a concrete reason.
- **Ask less.** Use sensible defaults, detect settings and generate internal
  identities. Ask people only for decisions the software cannot reasonably make.
- **Do the internal work in software.** Ordinary use should not require internal
  IDs, JSON files, copied checksums or a sequence of engineering commands. Keep
  necessary checks automatic and advanced settings out of the everyday path.
- **Make failures understandable.** Explain the problem and the next action.
  Retain valid answers and existing data so mistakes are easy to correct.
- **Keep the implementation and process small.** Extra components, configuration,
  restrictions, paperwork and approval steps need a demonstrated purpose.
- **Judge the real experience.** Follow the customer's published instructions.
  Passing tests and polished documentation do not excuse a complicated product.

Architects, coders, reviewers and future contributors must apply these principles
to all work. Correct unnecessary complexity within the existing delivery process;
do not create another bureaucracy to enforce simplicity. Preserve correct behavior
and customer data while keeping required internal steps inside the software.

These are the project's standards, not a claim that every prerelease workflow
already meets them. When something falls short, fix the experience.

[Back to Corolla](README.md)
