
#  π‘ Quiz App (μΌλ°μμ)


[ Demo](http://quiz1.jacobko.info/)

![quiz](https://user-images.githubusercontent.com/28912774/119346330-0a316f80-bcd5-11eb-8a63-38a7f70b2ca7.gif)



## π» 1.νλ‘μ νΈ μκ°  

### π μ¬μ©κΈ°μ  λ° μΈμ΄    

- Vanilla JS
- CSS
- HTML

### β° κ°λ° κΈ°κ°  
2021-05-17 ~ 24 


## π 2.νλ‘μ νΈ λ΄μ©

### μ£Όμ κΈ°λ₯

- κ°κ΄μ 5λ¬Έμ  λ₯Ό νλμ© νμ΄μ μ΅μ’μΌλ‘ λͺκ° λ§μ£Όμλμ§ μ€μ½μ΄ κ³μ°νμ¬ μΆλ ₯

- λ€μ νλ² λ (μ²μμΌλ‘ λμκ°μ) λ²νΌ ν΄λ¦­ μ, μ²μ λ¬Έμ λ‘ return 




## π 3.μ£Όμ μ½λ

```js
function loadQuiz() {

  deselectAnswers();

  const currentQuizData = quizData[currentQuiz]; // set currentQuizData

  // put into HTML from quizData
  questionEl.innerText = currentQuizData.question;
  a_text.innerText = currentQuizData.a;
  b_text.innerText = currentQuizData.b;
  c_text.innerText = currentQuizData.c;
  d_text.innerText = currentQuizData.d;
}

// execute loadQuiz
loadQuiz();

function getSelected() {

  let answer = undefined;

  answersEls.forEach((answerEl) => {
    if (answerEl.checked) {
      answer = answerEl.id;
    }
  });

  return answer;

}

function deselectAnswers() {
  answersEls.forEach((answerEl) => {
    answerEl.checked = false;
  })
}


// add click btn to change next question
submitBtn.addEventListener('click', () => {
  // check to see the answer
  const answer = getSelected();

  if (answer) {
    if (answer === quizData[currentQuiz].correct) {
      score++;
    }
    // after clicking, next index in quizData
    currentQuiz++;
    if (currentQuiz < quizData.length) loadQuiz();
    else {
      quiz.innerHTML = `
      <h2>λΉμ μ μ μλ.. ${score}/${quizData.length} μλλ€.</h2>
      <button onclick = "location.reload()">λ€μ νλ²λ!!</button>
      `
    }
  }
})
```

## 4. λλμ 

- ν΄μ¦ λ°μ΄ν°λ₯Ό μ¬λ¬ ν¨μλ₯Ό ν΅ν΄ (`loadQuiz()`, `getSelected()`, `deselectAnswers()`) λ¬Έμ , μ λ΅ μ JS quizdata λ₯Ό λΉκ΅νκ³  DOM μ μ¬μ©ν΄μ HTML λ¬Έμμ μΆλ ₯ νλλ²μ λ°°μ λλ°, ν¨μκ° μ¬λ¬κ°μ§κ° μλμ΄λμ μ½λλ₯Ό μ΄ν΄νλλ° μ΄λ €μμ΄ μμλ€.

- νλ¨λΆμ λ²νΌμ λ§λ€μ΄, click μ λ€μνμ΄μ§ μ ν λ° score ++ νλ€μ, μ΅μ’ νμ΄μ§μμ μ μλ₯Ό λνλ΄μ£Όμλ€. => λ λμκ°μλ μ ? νλ Έλμ§ λ¬Έμ μλν μ€λͺκ³Ό λͺλ² λ¬Έμ κ° νλ Έλμ§ μλ €μ£Όλ κΈ°λ₯μ νμ΅ νμ μΆκ° ν  μμ μ΄λ€.



## Reference

- [Florin Pop](https://www.youtube.com/watch?v=dtKciwk_si4&t=1788s)

- [Design Daily](https://www.uidesigndaily.com/posts/sketch-questionnaire-choice-submit-day-924)

- [Gradient Background colors](https://www.eggradients.com/)