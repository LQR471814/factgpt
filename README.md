# FactGPT

> Reduce mental corruption from interaction with AI tooling.

One of the use-cases for AI that had quickly gained rough
consensus of its superiority is LLM+web-search over Googling.

Using GPT instead of Google for your questions usually leads you
to the answers you want, lets you explore information much more
easily (if a sufficiently smart model is used), and allows you to
natively incorporate much more sophisticated context into a
question.

> [!NOTE]
> I am not talking about the Google search AI overview which seems
> to have been given a dumber model in exchange for latency. I
> mean a thinking model given a search tool, web content, and
> maybe a little bit of python.

I would argue that a significant portion of what you end up doing
with "LLM search" may spill out of reference and into learning.

What I mean by "learning" is any use of AI to guide yourself in
subject matters you are not an expert in. When you ask AI to
explain concepts, or help you solve a problem.

I believe the usage of LLMs to "learn" in this manner has many
pitfalls for education and training that are under-discussed. In
the spirit of prior "AI space" naming conventions, I will term
these pitfalls with a delightfully metaphorical and conceptually
overloaded name "mental corruption".

In a general sense, "mental corruption" simply refers to any
negative intellectual outcome that results from some activity.

As an example, consider "practice". Those who play an instrument
or a sport will know that practice will reinforce behaviors, but
not necessarily those that are correct. In particular, students
that practice incorrectly can often set themselves back, develop
bad habits that prohibit them from improving their performance,
which they may need to "unlearn" later. I would consider "bad
practice" to be a form of mental corruption.

Another example is "bad teachers" or "bad tutorials". Those who
receive conflicting, imprecise, or simply incorrect instruction
from educational materials or educators. This sort of dubious
reinforcement will cause the student to doubt their own knowledge,
implant imprecise or even inaccurate concepts in their mind,
memorize methods instead of principles, and create long-lasting
gaps in understanding that the student will need to work around.

This is "mental corruption" in the same sense that it actively
inhibits the student from making progress in their intellectual
development. And that if choosing a separate path for learning
without such "training", the student may be able to progress
further in the long-run otherwise.

Saying this more precisely, the efficacy of all "learning" depends
on who or where your feedback comes from.

Knowing all of this, it would be important for us to review the
reliability of LLMs as teachers first and foremost before using
them as such. In particular, the notion of "looks correct" should
not be the standard for correctness.

Here are some subtle correctness errors that are present in many
LLM responses. These same correctness errors will not appear in
textbooks, nor by domain experts, nor even by people who even know
a little bit about what they are doing.

- AI (by default) likes using metaphors, even in places where they
  are inappropriate or imprecise, it will also import phrases from
  other domains into domains where they are not used.
    - This is a correctness error because even if two concepts are
      "close-enough", that does not mean they are the same.
        - It also instills the incorrect habits into the student.
          If you were to talk to a domain expert using terminology
          not part of the domain. Even if the two have roughly the
          same meaning, the expert may not know what you mean
          (because they do not necessarily know what you do), this
          can cause unnecessary miscommunication.
        - For instance, you may conceptualize marginal cost as
          "the derivative of total cost" but an economist would
          probably find it confusing, because the two are not
          always equal and carry imply different "usages" of the
          concept.
        - This is not exclusive to AI, really it happens for many
          generalists, but AI being the "ultimate generalist"
          simply loves to do this, and thus reinforce it into all
          the new "AI-enhanced human generalists" of the world.
    - AI also likes inventing structure where it doesn't exist, I
      am sure you have seen it "classifying" actual pieces of
      information with bogus descriptions that hide nuance and
      imply things that
    - If you were to habitually treat two "close-enough" concepts
      as one and the same, you might also habitually forget to
      also communicate the details of their differences, which can
      cause miscommunication and misunderstanding.
    - All these behaviors are things that human experts will
      exhibit as well, but they are often heavily constrained and
      demarcated (with explicit mentions of where metaphors are or
      quotations of non-exact phrasing), and not treated
      literally, like standard terminology.
    - It seems like this sort of behavior is a compromise by the
      model creators to make the defaults more friendly for the
      average audience that is not trying to become an expert, but
      for those actively using the AI as a guide to learn how to
          speak the language of a domain or the precise details,
          this can be detrimental for their progress.
- AI itself is not necessarily an actual expert in every domain it
  knows about either. It very much exhibits the sort of behavior
  you see from an undergraduate who has taken an introductory
  course on a subject and attempts to use that knowledge to sound
  smart. (I am also guilty of this myself, that doesn't mean it is
  desirable behavior)
    - I will give an example:
        - ChatGPT 5.6 Sol. `WITHOUT WEB SEARCH OR TOOL CALLING.
          How does the "default" command work in Nushell`
            - This results in "correct" output.
            - `default fills missing or null values in
              record/table column. <input> | default <fallback>
              <column>`
        - ChatGPT 5.6 Sol. `WITHOUT WEB SEARCH OR TOOL CALLING.
          How can I set the default value of a nested value in a
          record in nushell`
            - This results in an example behavior that doesn't
              exist.
            - Specifically: `Use default with cell path ...
              $record | default 8080 config.port`
            - This doesn't actually work in Nushell (at the time
              of writing), it will simply create a key called
              `config.port` and give it the default value 8080,
              rather than updating the `port` field under the
              `config` field's value.
    - What I have just shown is called "hallucination", but is
      probably more precisely described as "over-fitting". What I
      want to illustrate though is not that hallucination exists
      or will always exist, but rather that any judgments
      regarding LLMs capabilities grounded on "appearance" are
      extremely flawed.
        - It is flawed to about the same level as software
          estimates. You "know" that whatever first comes out your
          mouth will need to be multiplied by 3 at minimum.
    - You might say that Nushell is simply not popular enough on
      the internet for the LLM to perform well on these tasks, but
      if that is the case then, how many tasks involve
          technologies that simply "aren't popular enough". How
          can I know if a task will be outside the range of AI's
          expertise without rigorously testing it myself? Only for
          it to surprise me in the strangest of ways that only
          show up in real-world workloads? In other words, AI's
          reliability is an open question that can only really be
          "known" in an ad-hoc sense.
    - On a macro level, this plain lack of understanding by LLMs
      in various domains but "appearance of understanding" (ex.
      networking, legal, healthcare) contributes to complete
      collapses in problem-solving capabilities even with thinking
      models that can "supposedly" reason their way to a solution
      given enough logical predicates. This is often called as
      "failing to reason beyond the distribution" and is often the
      result of over-fitting.
        - Note: Harnesses will not be of much help here either.
          Verification and loops can only help the AI not give you
          a broken demo, given that it eventually finishes. If the
          AI lacks the requisite knowledge to even finish within a
          reasonable amount of time and tokens, then you must
          simply call that a failure. And even if the AI is given
          answers from a domain expert, you will simply run into
          the same issues of failing to reason beyond the
          distribution when you run into new problems that do not
          have them.

For all of my complaints, you might say that "well its performance
is 'good enough' *for this task* or *for my purposes*" and that is
all well and good, I trust that you know your circumstances the
best. However, I must warn that consistency which is "good enough"
"on the job" or in real world cases with safeguards and validation
is not the same level of consistency that is required to bequeath
students with an understanding that will be built upon, that which
is commonly known as "education".

AI also gives you the itch to just use it and bypass learning
entirely. At its extremes, it can induce a subtle form of "learned
helplessness", where one becomes unable to do anything themselves
or habitually wastes opportunities for growth. Why, the first rule
of optimizing anything is to simply to "do less", now consider the
prospect of using AI to "optimize learning". It should be easy to
see how this can be detrimental to the development of human
capital.

Then there may be arguments that focusing on human capital is
incorrect to begin with and that one should dive first into "fully
utilizing AI". These arguments I find unconvincing, primarily due
to the fact that the formulated relationship is "you need AI", "AI
does not need you".

Now I am also well aware that modern AI platforms will have what
is known as "learning modes", where the goal is to have the AI
help the user learn information incrementally without assuming the
user is already an expert.

Though, my problem with these "learning modes" (outside everything
I've already mentioned) is also something that the LLM itself
often has trouble with, namely sycophancy and re-framing problems.

Let's suppose I ask Gemini in the "guided learning" mode to give
me a "difficult problem, supposing that I am learning python". It
directly jumps into asking me to implement the "longest substring
without repeating characters".

If I were asked the same thing, I would immediately ask the user
back: "Ok, what parts of Python are you learning right now, and
what do you want me to test you on?" Because what is "difficult"
in the ("learning Python internals" sense) is way different from
what is "difficult" in the ("learning DSA and Python is
convenient" sense). In fact, for DSA I would probably recommend
you C. There is no "average" answer to this question, I cannot
give you a single answer without compromising the correctness of
any single answer I could possibly give, so I have to obtain more
context.

AI simply doesn't do this by default, you can explicitly prompt it
to do so, and it will help, but AI generally has a hard time
escaping incorrect or vague framing to begin with. Similarly, it
has been observed that contradictions or plain vague instructions
within a prompt will heavily degrade AI performance? A student is
extremely likely to ask questions with incorrect framing! This is
the purpose of a teacher, but if the teacher always tries to
answer the question within the student's own framing, or in a way
that matches the student's framing without any push back, then the
teaching becomes much less effective. Pushing back on framing has
been massively improved in AI even relative to how it was a year
ago, but it still remains a prominent failure mode.

In any case, I am interested in mitigating the sort of "mental
corruption" effects of AI while still being able to speed up
mechanical search and lookup. The [system prompt](./prompt.md)
in this repository is an attempt at doing so.

> [!NOTE]
> Like any form of "prompt engineering", you should take its
> literal text content with a grain of salt, rather focus on the
> patterns it describes and perhaps consider deterministic (or
> more reliable) methods to enforce those rules independently.

> [!NOTE]
> I also included an additional section based on [caveman](https://github.com/JuliusBrussee/caveman) to
> cut down on "yap" and reduce output latency, it is not necessary
> for replicating the expected behavior.

The way it works is very much based on the idea of weaning the
human off of the "unreliable feedback" which can be AI output.
Specifically, it attempts to:

- Remove excessive framing, "executive summaries", and "next
  steps" created by overeager AI. Many of which can be faulty,
  needlessly extends response length, are often unasked for, and
  can stop the human from using their brain.
- Let the AI clearly delineate what information comes from its
  "training data" and that which comes from the sources it looked
  up. If this works correctly, this should prevent the human from
  making judgments based on thin-air.
- Stop using metaphors or importing terminology from different
  disciplines.
- ["Make no mistakes."](https://www.businessinsider.com/claude-cowork-memes-2026-1)

I am very much aware that prompt engineering itself is very faulty
so this "prompt/skill" is by no means a silver bullet, but I hope
that it at least tips the scales towards less "mental corruption"
for the time being.

