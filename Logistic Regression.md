back to main page

# Logistic Regression

## Intro to Logistic Regression

Logistic regression is a statistical and machine learning technique for <u>**classifying**</u> records of a dataset based on the values of the input fields. Despite its name, is a linear model for classification rather than regression. Logistic regression is also known in the literature as *logit regression*, *maximum-entropy classification (MaxEnt)* or the *log-linear classifier*. 
- Can be used for both binary classification and multi-class classification.
- Can not only predict the class of each case, we also measure the probability of a case belonging to a specific class.
- It is analogous to linear regression, but tries to predict a categorical or discrete target field instead of a numeric one. In linear regression, we might try to predict a continuous value of variables such as the price of a house, or fuel consumption of a car, etc. But in logistic regression, we predict a variable which is binary such as yes/no, true/false, successful or not successful, and so on, all of which can be coded as zero or one.
- In logistic regression dependent variables should be Numerical. If categorical, they should be dummy or indicator coded. 


## When should we use logistic regression? 
Here are four situations in which logistic regression is a good candidate: 
1) When the target field in your data is categorical or specifically is binary. 
2) You need the probability of your prediction. Logistic regression returns a probability score between zero and one. 
3) If your data is linearly separable. The decision boundary of logistic regression is a line or a plane or a hyper plane. A classifier will classify all the points on one side of the decision boundary as belonging to one class, and all those on the other side as belonging to the other class. (Please note that in using logistic regression, we can also achieve a complex decision boundary using polynomial processing as well)
4) You need to understand the impact of a feature. After finding the optimum parameters, a feature X with the weight Theta one close to zero has a smaller effect on the prediction than features with large absolute values of Theta one. Indeed, it allows us to understand the impact an independent variable has on the dependent variable while controlling other independent variables. 

## Logistic function 

<p>An explanation of logistic regression can begin with an explanation of the standard <a href="/wiki/Logistic_function" title="Logistic function">logistic function</a>. The logistic function is a <a href="/wiki/Sigmoid_function" title="Sigmoid function">sigmoid function</a>, which takes any <a href="/wiki/Real_number" title="Real number">real</a> input <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:0.84ex; height:2.009ex;" alt="t"/></span>, (<span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t\in \mathbb {R} }">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
        <mo>&#x2208;<!-- ∈ --></mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi mathvariant="double-struck">R</mi>
        </mrow>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t\in \mathbb {R} }</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/592bced0c39b10fc90e74c6a66223abfbfb029de" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:5.358ex; height:2.176ex;" alt="{\displaystyle t\in \mathbb {R} }"/></span>), and outputs a value between zero and one;<sup id="cite_ref-Hosmer_15-2" class="reference"><a href="#cite_note-Hosmer-15">&#91;15&#93;</a></sup> for the logit, this is interpreted as taking input <a href="/wiki/Log-odds" class="mw-redirect" title="Log-odds">log-odds</a> and having output <a href="/wiki/Probability" title="Probability">probability</a>. The <i>standard</i> logistic function <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \sigma :\mathbb {R} \rightarrow (0,1)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>&#x03C3;<!-- σ --></mi>
        <mo>:</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi mathvariant="double-struck">R</mi>
        </mrow>
        <mo stretchy="false">&#x2192;<!-- → --></mo>
        <mo stretchy="false">(</mo>
        <mn>0</mn>
        <mo>,</mo>
        <mn>1</mn>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \sigma :\mathbb {R} \rightarrow (0,1)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/327e60eac9c4e38d6d67fd4864645758a29b43a5" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; width:13.727ex; height:2.843ex;" alt="{\displaystyle \sigma :\mathbb {R} \rightarrow (0,1)}"/></span> is defined as follows:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \sigma (t)={\frac {e^{t}}{e^{t}+1}}={\frac {1}{1+e^{-t}}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>&#x03C3;<!-- σ --></mi>
        <mo stretchy="false">(</mo>
        <mi>t</mi>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <msup>
              <mi>e</mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mi>t</mi>
              </mrow>
            </msup>
            <mrow>
              <msup>
                <mi>e</mi>
                <mrow class="MJX-TeXAtom-ORD">
                  <mi>t</mi>
                </mrow>
              </msup>
              <mo>+</mo>
              <mn>1</mn>
            </mrow>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mn>1</mn>
            <mrow>
              <mn>1</mn>
              <mo>+</mo>
              <msup>
                <mi>e</mi>
                <mrow class="MJX-TeXAtom-ORD">
                  <mo>&#x2212;<!-- − --></mo>
                  <mi>t</mi>
                </mrow>
              </msup>
            </mrow>
          </mfrac>
        </mrow>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \sigma (t)={\frac {e^{t}}{e^{t}+1}}={\frac {1}{1+e^{-t}}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/5e648e1dd38ef843d57777cd34c67465bbca694f" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.171ex; width:24.951ex; height:5.843ex;" alt="\sigma (t)={\frac {e^{t}}{e^{t}+1}}={\frac {1}{1+e^{-t}}}"/></span></dd></dl>
<p>A graph of the logistic function on the <i>t</i>-interval (−6,6) is shown in Figure 1.
</p><p>Let us assume that <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:0.84ex; height:2.009ex;" alt="t"/></span> is a linear function of a single <a href="/wiki/Dependent_and_independent_variables" title="Dependent and independent variables">explanatory variable</a> <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.33ex; height:1.676ex;" alt="x"/></span> (the case where <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:0.84ex; height:2.009ex;" alt="t"/></span> is a <i>linear combination</i> of multiple explanatory variables is treated similarly). We can then express <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/65658b7b223af9e1acc877d848888ecdb4466560" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:0.84ex; height:2.009ex;" alt="t"/></span> as follows:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle t=\beta _{0}+\beta _{1}x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>t</mi>
        <mo>=</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle t=\beta _{0}+\beta _{1}x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/836d93163447344be4715ec00638c1cd829e376c" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:12.848ex; height:2.509ex;" alt="t=\beta _{0}+\beta _{1}x"/></span></dd></dl>
<p>And the general logistic function <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p:\mathbb {R} \rightarrow (0,1)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo>:</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mi mathvariant="double-struck">R</mi>
        </mrow>
        <mo stretchy="false">&#x2192;<!-- → --></mo>
        <mo stretchy="false">(</mo>
        <mn>0</mn>
        <mo>,</mo>
        <mn>1</mn>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p:\mathbb {R} \rightarrow (0,1)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/4687bcc1936d9b9a4d1562edeb8dc58b34519821" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; margin-left: -0.089ex; width:13.656ex; height:2.843ex;" alt="{\displaystyle p:\mathbb {R} \rightarrow (0,1)}"/></span>can now be written as:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p(x)=\sigma (t)={\frac {1}{1+e^{-(\beta _{0}+\beta _{1}x)}}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <mi>&#x03C3;<!-- σ --></mi>
        <mo stretchy="false">(</mo>
        <mi>t</mi>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mn>1</mn>
            <mrow>
              <mn>1</mn>
              <mo>+</mo>
              <msup>
                <mi>e</mi>
                <mrow class="MJX-TeXAtom-ORD">
                  <mo>&#x2212;<!-- − --></mo>
                  <mo stretchy="false">(</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>0</mn>
                    </mrow>
                  </msub>
                  <mo>+</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>1</mn>
                    </mrow>
                  </msub>
                  <mi>x</mi>
                  <mo stretchy="false">)</mo>
                </mrow>
              </msup>
            </mrow>
          </mfrac>
        </mrow>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p(x)=\sigma (t)={\frac {1}{1+e^{-(\beta _{0}+\beta _{1}x)}}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/e376fe69caee24c914fab1360de36900b7bb9c24" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.338ex; margin-left: -0.089ex; width:29.029ex; height:5.676ex;" alt="{\displaystyle p(x)=\sigma (t)={\frac {1}{1+e^{-(\beta _{0}+\beta _{1}x)}}}}"/></span></dd></dl>
<p>In the logistic model, <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p(x)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p(x)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8cb7afced134ef75572e5314a5d278c2d644f438" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; margin-left: -0.089ex; width:4.398ex; height:2.843ex;" alt="p(x)"/></span> is interpreted as the probability of the dependent variable <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle Y}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>Y</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle Y}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/961d67d6b454b4df2301ac571808a3538b3a6d3f" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.171ex; width:1.773ex; height:2.009ex;" alt="Y"/></span> equaling a success/case rather than a failure/non-case. It's clear that the <a href="/wiki/Dependent_and_independent_variables" title="Dependent and independent variables">response variables</a> <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle Y_{i}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>Y</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle Y_{i}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/d57be496fff95ee2a97ee43c7f7fe244b4dbf8ae" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:2.15ex; height:2.509ex;" alt="Y_{i}"/></span> are not identically distributed: <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle P(Y_{i}=1\mid X)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>P</mi>
        <mo stretchy="false">(</mo>
        <msub>
          <mi>Y</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
          </mrow>
        </msub>
        <mo>=</mo>
        <mn>1</mn>
        <mo>&#x2223;<!-- ∣ --></mo>
        <mi>X</mi>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle P(Y_{i}=1\mid X)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/6b15fb14aa841ab1d415b65d2058f0c1212e9125" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; width:13.883ex; height:2.843ex;" alt="P(Y_{i}=1\mid X)"/></span> differs from one data point <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle X_{i}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>X</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle X_{i}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/af4a0955af42beb5f85aa05fb8c07abedc13990d" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:2.724ex; height:2.509ex;" alt="X_{i}"/></span> to another, though they are independent given <a href="/wiki/Design_matrix" title="Design matrix">design matrix</a> <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle X}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>X</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle X}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/68baa052181f707c662844a465bfeeb135e82bab" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.98ex; height:2.176ex;" alt="X"/></span> and shared parameters <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta }">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>&#x03B2;<!-- β --></mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta }</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/7ed48a5e36207156fb792fa79d29925d2f7901e8" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:1.332ex; height:2.509ex;" alt="\beta "/></span>.<sup id="cite_ref-Freedman09_9-1" class="reference"><a href="#cite_note-Freedman09-9">&#91;9&#93;</a></sup>
</p>
<h3><span class="mw-headline" id="Definition_of_the_inverse_of_the_logistic_function">Definition of the inverse of the logistic function</span><span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=Logistic_regression&amp;action=edit&amp;section=10" title="Edit section: Definition of the inverse of the logistic function">edit</a><span class="mw-editsection-bracket">]</span></span></h3>
<p>We can now define the <a href="/wiki/Logit" title="Logit">logit</a> (log odds) function as the inverse <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle g=\sigma ^{-1}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>g</mi>
        <mo>=</mo>
        <msup>
          <mi>&#x03C3;<!-- σ --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mo>&#x2212;<!-- − --></mo>
            <mn>1</mn>
          </mrow>
        </msup>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle g=\sigma ^{-1}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/74af9b48e275a7ed04881fe9e406306500bd7dd6" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:7.878ex; height:3.009ex;" alt="{\displaystyle g=\sigma ^{-1}}"/></span> of the standard logistic function. It is easy to see that it satisfies:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle g(p(x))=\sigma ^{-1}(p(x))=\operatorname {logit} p(x)=\ln \left({\frac {p(x)}{1-p(x)}}\right)=\beta _{0}+\beta _{1}x,}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>g</mi>
        <mo stretchy="false">(</mo>
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <msup>
          <mi>&#x03C3;<!-- σ --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mo>&#x2212;<!-- − --></mo>
            <mn>1</mn>
          </mrow>
        </msup>
        <mo stretchy="false">(</mo>
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <mi>logit</mi>
        <mo>&#x2061;<!-- ⁡ --></mo>
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
        <mo>=</mo>
        <mi>ln</mi>
        <mo>&#x2061;<!-- ⁡ --></mo>
        <mrow>
          <mo>(</mo>
          <mrow class="MJX-TeXAtom-ORD">
            <mfrac>
              <mrow>
                <mi>p</mi>
                <mo stretchy="false">(</mo>
                <mi>x</mi>
                <mo stretchy="false">)</mo>
              </mrow>
              <mrow>
                <mn>1</mn>
                <mo>&#x2212;<!-- − --></mo>
                <mi>p</mi>
                <mo stretchy="false">(</mo>
                <mi>x</mi>
                <mo stretchy="false">)</mo>
              </mrow>
            </mfrac>
          </mrow>
          <mo>)</mo>
        </mrow>
        <mo>=</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mi>x</mi>
        <mo>,</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle g(p(x))=\sigma ^{-1}(p(x))=\operatorname {logit} p(x)=\ln \left({\frac {p(x)}{1-p(x)}}\right)=\beta _{0}+\beta _{1}x,}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/d5e8b239c25debd50d089a064d3b902c21391575" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.671ex; width:62.692ex; height:6.509ex;" alt="{\displaystyle g(p(x))=\sigma ^{-1}(p(x))=\operatorname {logit} p(x)=\ln \left({\frac {p(x)}{1-p(x)}}\right)=\beta _{0}+\beta _{1}x,}"/></span></dd></dl>
<p>and equivalently, after exponentiating both sides we have the odds:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle {\frac {p(x)}{1-p(x)}}=e^{\beta _{0}+\beta _{1}x}.}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mrow>
              <mi>p</mi>
              <mo stretchy="false">(</mo>
              <mi>x</mi>
              <mo stretchy="false">)</mo>
            </mrow>
            <mrow>
              <mn>1</mn>
              <mo>&#x2212;<!-- − --></mo>
              <mi>p</mi>
              <mo stretchy="false">(</mo>
              <mi>x</mi>
              <mo stretchy="false">)</mo>
            </mrow>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <msup>
          <mi>e</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>0</mn>
              </mrow>
            </msub>
            <mo>+</mo>
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>1</mn>
              </mrow>
            </msub>
            <mi>x</mi>
          </mrow>
        </msup>
        <mo>.</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle {\frac {p(x)}{1-p(x)}}=e^{\beta _{0}+\beta _{1}x}.}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/504648d8b5e4bc600a26f4094d13b4dde104d643" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.671ex; width:19.951ex; height:6.509ex;" alt="{\displaystyle {\frac {p(x)}{1-p(x)}}=e^{\beta _{0}+\beta _{1}x}.}"/></span></dd></dl>
<h3><span class="mw-headline" id="Interpretation_of_these_terms">Interpretation of these terms</span><span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=Logistic_regression&amp;action=edit&amp;section=11" title="Edit section: Interpretation of these terms">edit</a><span class="mw-editsection-bracket">]</span></span></h3>
<p>In the above equations, the terms are as follows:
</p>
<ul><li><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle g}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>g</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle g}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/d3556280e66fe2c0d0140df20935a6f057381d77" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:1.116ex; height:2.009ex;" alt="g"/></span> is the logit function. The equation for <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle g(p(x))}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>g</mi>
        <mo stretchy="false">(</mo>
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle g(p(x))}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/9d8ae4abe22d4ff74e61b963a849fc42e04e8975" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; width:7.234ex; height:2.843ex;" alt="{\displaystyle g(p(x))}"/></span> illustrates that the <a href="/wiki/Logit" title="Logit">logit</a> (i.e., log-odds or natural logarithm of the odds) is equivalent to the linear regression expression.</li>
<li><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \ln }">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>ln</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \ln }</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/c0de5ba4f372ede555d00035e70c50ed0b9625d0" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.939ex; height:2.176ex;" alt="\ln "/></span> denotes the <a href="/wiki/Natural_logarithm" title="Natural logarithm">natural logarithm</a>.</li>
<li><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p(x)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p(x)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8cb7afced134ef75572e5314a5d278c2d644f438" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; margin-left: -0.089ex; width:4.398ex; height:2.843ex;" alt="p(x)"/></span> is the probability that the dependent variable equals a case, given some linear combination of the predictors. The formula for <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p(x)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p(x)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8cb7afced134ef75572e5314a5d278c2d644f438" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; margin-left: -0.089ex; width:4.398ex; height:2.843ex;" alt="p(x)"/></span> illustrates that the probability of the dependent variable equaling a case is equal to the value of the logistic function of the linear regression expression. This is important in that it shows that the value of the linear regression expression can vary from negative to positive infinity and yet, after transformation, the resulting expression for the probability <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p(x)}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo stretchy="false">(</mo>
        <mi>x</mi>
        <mo stretchy="false">)</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p(x)}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8cb7afced134ef75572e5314a5d278c2d644f438" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.838ex; margin-left: -0.089ex; width:4.398ex; height:2.843ex;" alt="p(x)"/></span> ranges between 0 and 1.</li>
<li><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{0}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{0}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/40b42f71f244103a8fca3c76885c7580a92831c8" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:2.37ex; height:2.509ex;" alt="\beta _{0}"/></span> is the <a href="/wiki/Y-intercept" title="Y-intercept">intercept</a> from the linear regression equation (the value of the criterion when the predictor is equal to zero).</li>
<li><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{1}x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{1}x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8054fed54c314532ef4e5105b6edd0eb65a378e7" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:3.7ex; height:2.509ex;" alt="\beta _{1}x"/></span> is the regression coefficient multiplied by some value of the predictor.</li>
<li>base <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle e}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>e</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle e}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/cd253103f0876afc68ebead27a5aa9867d927467" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.083ex; height:1.676ex;" alt="e"/></span> denotes the exponential function.</li></ul>
<h3><span class="mw-headline" id="Definition_of_the_odds">Definition of the odds</span><span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=Logistic_regression&amp;action=edit&amp;section=12" title="Edit section: Definition of the odds">edit</a><span class="mw-editsection-bracket">]</span></span></h3>
<p>The odds of the dependent variable equaling a case (given some linear combination <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.33ex; height:1.676ex;" alt="x"/></span> of the predictors) is equivalent to the exponential function of the linear regression expression. This illustrates how the <a href="/wiki/Logit" title="Logit">logit</a> serves as a link function between the probability and the linear regression expression. Given that the logit ranges between negative and positive infinity, it provides an adequate criterion upon which to conduct linear regression and the logit is easily converted back into the odds.<sup id="cite_ref-Hosmer_15-3" class="reference"><a href="#cite_note-Hosmer-15">&#91;15&#93;</a></sup>
</p><p>So we define odds of the dependent variable equaling a case (given some linear combination <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/87f9e315fd7e2ba406057a97300593c4802b53e4" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:1.33ex; height:1.676ex;" alt="x"/></span> of the predictors) as follows:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle {\text{odds}}=e^{\beta _{0}+\beta _{1}x}.}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mrow class="MJX-TeXAtom-ORD">
          <mtext>odds</mtext>
        </mrow>
        <mo>=</mo>
        <msup>
          <mi>e</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>0</mn>
              </mrow>
            </msub>
            <mo>+</mo>
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>1</mn>
              </mrow>
            </msub>
            <mi>x</mi>
          </mrow>
        </msup>
        <mo>.</mo>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle {\text{odds}}=e^{\beta _{0}+\beta _{1}x}.}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/8b5acc9cf67be7974971e0f520029f356969ba90" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:15.467ex; height:2.676ex;" alt="{\text{odds}}=e^{\beta _{0}+\beta _{1}x}."/></span></dd></dl>
<h3><span class="mw-headline" id="The_odds_ratio">The odds ratio</span><span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=Logistic_regression&amp;action=edit&amp;section=13" title="Edit section: The odds ratio">edit</a><span class="mw-editsection-bracket">]</span></span></h3>
<p>For a continuous independent variable the odds ratio can be defined as:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \mathrm {OR} ={\frac {\operatorname {odds} (x+1)}{\operatorname {odds} (x)}}={\frac {\left({\frac {F(x+1)}{1-F(x+1)}}\right)}{\left({\frac {F(x)}{1-F(x)}}\right)}}={\frac {e^{\beta _{0}+\beta _{1}(x+1)}}{e^{\beta _{0}+\beta _{1}x}}}=e^{\beta _{1}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mrow class="MJX-TeXAtom-ORD">
          <mi mathvariant="normal">O</mi>
          <mi mathvariant="normal">R</mi>
        </mrow>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mrow>
              <mi>odds</mi>
              <mo>&#x2061;<!-- ⁡ --></mo>
              <mo stretchy="false">(</mo>
              <mi>x</mi>
              <mo>+</mo>
              <mn>1</mn>
              <mo stretchy="false">)</mo>
            </mrow>
            <mrow>
              <mi>odds</mi>
              <mo>&#x2061;<!-- ⁡ --></mo>
              <mo stretchy="false">(</mo>
              <mi>x</mi>
              <mo stretchy="false">)</mo>
            </mrow>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mrow>
              <mo>(</mo>
              <mrow class="MJX-TeXAtom-ORD">
                <mfrac>
                  <mrow>
                    <mi>F</mi>
                    <mo stretchy="false">(</mo>
                    <mi>x</mi>
                    <mo>+</mo>
                    <mn>1</mn>
                    <mo stretchy="false">)</mo>
                  </mrow>
                  <mrow>
                    <mn>1</mn>
                    <mo>&#x2212;<!-- − --></mo>
                    <mi>F</mi>
                    <mo stretchy="false">(</mo>
                    <mi>x</mi>
                    <mo>+</mo>
                    <mn>1</mn>
                    <mo stretchy="false">)</mo>
                  </mrow>
                </mfrac>
              </mrow>
              <mo>)</mo>
            </mrow>
            <mrow>
              <mo>(</mo>
              <mrow class="MJX-TeXAtom-ORD">
                <mfrac>
                  <mrow>
                    <mi>F</mi>
                    <mo stretchy="false">(</mo>
                    <mi>x</mi>
                    <mo stretchy="false">)</mo>
                  </mrow>
                  <mrow>
                    <mn>1</mn>
                    <mo>&#x2212;<!-- − --></mo>
                    <mi>F</mi>
                    <mo stretchy="false">(</mo>
                    <mi>x</mi>
                    <mo stretchy="false">)</mo>
                  </mrow>
                </mfrac>
              </mrow>
              <mo>)</mo>
            </mrow>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <msup>
              <mi>e</mi>
              <mrow class="MJX-TeXAtom-ORD">
                <msub>
                  <mi>&#x03B2;<!-- β --></mi>
                  <mrow class="MJX-TeXAtom-ORD">
                    <mn>0</mn>
                  </mrow>
                </msub>
                <mo>+</mo>
                <msub>
                  <mi>&#x03B2;<!-- β --></mi>
                  <mrow class="MJX-TeXAtom-ORD">
                    <mn>1</mn>
                  </mrow>
                </msub>
                <mo stretchy="false">(</mo>
                <mi>x</mi>
                <mo>+</mo>
                <mn>1</mn>
                <mo stretchy="false">)</mo>
              </mrow>
            </msup>
            <msup>
              <mi>e</mi>
              <mrow class="MJX-TeXAtom-ORD">
                <msub>
                  <mi>&#x03B2;<!-- β --></mi>
                  <mrow class="MJX-TeXAtom-ORD">
                    <mn>0</mn>
                  </mrow>
                </msub>
                <mo>+</mo>
                <msub>
                  <mi>&#x03B2;<!-- β --></mi>
                  <mrow class="MJX-TeXAtom-ORD">
                    <mn>1</mn>
                  </mrow>
                </msub>
                <mi>x</mi>
              </mrow>
            </msup>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <msup>
          <mi>e</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>1</mn>
              </mrow>
            </msub>
          </mrow>
        </msup>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \mathrm {OR} ={\frac {\operatorname {odds} (x+1)}{\operatorname {odds} (x)}}={\frac {\left({\frac {F(x+1)}{1-F(x+1)}}\right)}{\left({\frac {F(x)}{1-F(x)}}\right)}}={\frac {e^{\beta _{0}+\beta _{1}(x+1)}}{e^{\beta _{0}+\beta _{1}x}}}=e^{\beta _{1}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/18dc1087bc50b9c1afee6820aad1858704b43ea3" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -4.505ex; width:55.006ex; height:10.176ex;" alt="{\displaystyle \mathrm {OR} ={\frac {\operatorname {odds} (x+1)}{\operatorname {odds} (x)}}={\frac {\left({\frac {F(x+1)}{1-F(x+1)}}\right)}{\left({\frac {F(x)}{1-F(x)}}\right)}}={\frac {e^{\beta _{0}+\beta _{1}(x+1)}}{e^{\beta _{0}+\beta _{1}x}}}=e^{\beta _{1}}}"/></span></dd></dl>
<p>This exponential relationship provides an interpretation for <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{1}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{1}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/eeeccd8b585b819e38f9c1fe5e9816a3ea01804c" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:2.37ex; height:2.509ex;" alt="\beta _{1}"/></span>: The odds multiply by <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle e^{\beta _{1}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msup>
          <mi>e</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <msub>
              <mi>&#x03B2;<!-- β --></mi>
              <mrow class="MJX-TeXAtom-ORD">
                <mn>1</mn>
              </mrow>
            </msub>
          </mrow>
        </msup>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle e^{\beta _{1}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/2525a52012c4903148201b741a010bb7f2f4197b" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:3.078ex; height:2.676ex;" alt="e^{\beta _{1}}"/></span> for every 1-unit increase in x.<sup id="cite_ref-20" class="reference"><a href="#cite_note-20">&#91;20&#93;</a></sup>
</p><p>For a binary independent variable the odds ratio is defined as <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle {\frac {ad}{bc}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mrow>
              <mi>a</mi>
              <mi>d</mi>
            </mrow>
            <mrow>
              <mi>b</mi>
              <mi>c</mi>
            </mrow>
          </mfrac>
        </mrow>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle {\frac {ad}{bc}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/bf85a97636710d178d1802494a36c36d12f02ad1" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.005ex; width:3.282ex; height:5.509ex;" alt="{\frac {ad}{bc}}"/></span> where <i>a</i>, <i>b</i>, <i>c</i> and <i>d</i> are cells in a 2×2 <a href="/wiki/Contingency_table" title="Contingency table">contingency table</a>.<sup id="cite_ref-21" class="reference"><a href="#cite_note-21">&#91;21&#93;</a></sup>
</p>
<h3><span class="mw-headline" id="Multiple_explanatory_variables">Multiple explanatory variables</span><span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=Logistic_regression&amp;action=edit&amp;section=14" title="Edit section: Multiple explanatory variables">edit</a><span class="mw-editsection-bracket">]</span></span></h3>
<p>If there are multiple explanatory variables, the above expression <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{0}+\beta _{1}x}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mi>x</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{0}+\beta _{1}x}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/413f0918db1f01e559350b98d49ee22be2f36dea" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.671ex; width:8.91ex; height:2.509ex;" alt="\beta _{0}+\beta _{1}x"/></span> can be revised to <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}=\beta _{0}+\sum _{i=1}^{m}\beta _{i}x_{i}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>2</mn>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>2</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <mo>&#x22EF;<!-- ⋯ --></mo>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>m</mi>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>m</mi>
          </mrow>
        </msub>
        <mo>=</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <munderover>
          <mo>&#x2211;<!-- ∑ --></mo>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
            <mo>=</mo>
            <mn>1</mn>
          </mrow>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>m</mi>
          </mrow>
        </munderover>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>i</mi>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}=\beta _{0}+\sum _{i=1}^{m}\beta _{i}x_{i}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/faa7cfcfb9f91ae36fcd35766373bf48c094be85" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -3.005ex; width:48.254ex; height:6.843ex;" alt="{\displaystyle \beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}=\beta _{0}+\sum _{i=1}^{m}\beta _{i}x_{i}}"/></span>. Then when this is used in the equation relating the log odds of a success to the values of the predictors, the linear regression will be a <a href="/wiki/Multiple_regression" class="mw-redirect" title="Multiple regression">multiple regression</a> with <i>m</i> explanators; the parameters <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \beta _{j}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>j</mi>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \beta _{j}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/83edf0558c67ad56ca5c05096b550bd733d62c4b" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -1.005ex; width:2.225ex; height:2.843ex;" alt="\beta _{j}"/></span> for all <i>j</i> = 0, 1, 2, ..., <i>m</i> are all estimated.
</p><p>Again, the more traditional equations are:
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle \log {\frac {p}{1-p}}=\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>log</mi>
        <mo>&#x2061;<!-- ⁡ --></mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mi>p</mi>
            <mrow>
              <mn>1</mn>
              <mo>&#x2212;<!-- − --></mo>
              <mi>p</mi>
            </mrow>
          </mfrac>
        </mrow>
        <mo>=</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>0</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>1</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>2</mn>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mn>2</mn>
          </mrow>
        </msub>
        <mo>+</mo>
        <mo>&#x22EF;<!-- ⋯ --></mo>
        <mo>+</mo>
        <msub>
          <mi>&#x03B2;<!-- β --></mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>m</mi>
          </mrow>
        </msub>
        <msub>
          <mi>x</mi>
          <mrow class="MJX-TeXAtom-ORD">
            <mi>m</mi>
          </mrow>
        </msub>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle \log {\frac {p}{1-p}}=\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/c6fbaf6182755b528d3232d60408a2414b6d76c1" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.338ex; width:44.424ex; height:5.343ex;" alt="{\displaystyle \log {\frac {p}{1-p}}=\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m}}"/></span></dd></dl>
<p>and
</p>
<dl><dd><span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle p={\frac {1}{1+b^{-(\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m})}}}}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>p</mi>
        <mo>=</mo>
        <mrow class="MJX-TeXAtom-ORD">
          <mfrac>
            <mn>1</mn>
            <mrow>
              <mn>1</mn>
              <mo>+</mo>
              <msup>
                <mi>b</mi>
                <mrow class="MJX-TeXAtom-ORD">
                  <mo>&#x2212;<!-- − --></mo>
                  <mo stretchy="false">(</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>0</mn>
                    </mrow>
                  </msub>
                  <mo>+</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>1</mn>
                    </mrow>
                  </msub>
                  <msub>
                    <mi>x</mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>1</mn>
                    </mrow>
                  </msub>
                  <mo>+</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>2</mn>
                    </mrow>
                  </msub>
                  <msub>
                    <mi>x</mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mn>2</mn>
                    </mrow>
                  </msub>
                  <mo>+</mo>
                  <mo>&#x22EF;<!-- ⋯ --></mo>
                  <mo>+</mo>
                  <msub>
                    <mi>&#x03B2;<!-- β --></mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mi>m</mi>
                    </mrow>
                  </msub>
                  <msub>
                    <mi>x</mi>
                    <mrow class="MJX-TeXAtom-ORD">
                      <mi>m</mi>
                    </mrow>
                  </msub>
                  <mo stretchy="false">)</mo>
                </mrow>
              </msup>
            </mrow>
          </mfrac>
        </mrow>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle p={\frac {1}{1+b^{-(\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m})}}}}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/da88d81e6a0169ec2da7d7bc0e0f4efef4b9e2c7" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -2.338ex; margin-left: -0.089ex; width:33.395ex; height:5.676ex;" alt="{\displaystyle p={\frac {1}{1+b^{-(\beta _{0}+\beta _{1}x_{1}+\beta _{2}x_{2}+\cdots +\beta _{m}x_{m})}}}}"/></span></dd></dl>
<p>where usually <span class="mwe-math-element"><span class="mwe-math-mathml-inline mwe-math-mathml-a11y" style="display: none;"><math xmlns="http://www.w3.org/1998/Math/MathML"  alttext="{\displaystyle b=e}">
  <semantics>
    <mrow class="MJX-TeXAtom-ORD">
      <mstyle displaystyle="true" scriptlevel="0">
        <mi>b</mi>
        <mo>=</mo>
        <mi>e</mi>
      </mstyle>
    </mrow>
    <annotation encoding="application/x-tex">{\displaystyle b=e}</annotation>
  </semantics>
</math></span><img src="https://wikimedia.org/api/rest_v1/media/math/render/svg/bc20630fca3169208fadd9eb539de8de26b045d0" class="mwe-math-fallback-image-inline" aria-hidden="true" style="vertical-align: -0.338ex; width:5.18ex; height:2.176ex;" alt="{\displaystyle b=e}"/></span>.
</p>

## Logistic Regression vs Linear Regression


The *sigmoid function*, also called the *logistic function*, 



